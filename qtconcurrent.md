# Qt Concurrent 개요

QtConcurrent는 Array형태의 자료형의 각 요소에 대해

일련의 함수를 병렬적으로 실행함과동시에 이를 비동기적으로 처리해주는 라이브러리임

- 지원되는 Array: QList, QVector, std::vector

이중 QList를 사용 예정

> TODO: 세개의 벤치마크 비교

QtConcurrent는 계산함수와 결과출력자로 구분됨(가칭)

> TODO: 더 좋은 Naming이 있으면 수정할것

계산함수는 세 가지 계열로 분류됨

1. Map계열 Map and Map-Reduce

2. Filter계열 Filter and Filter-Reduce

3. Run계열

결과출력자는 다음으로 구성됨

1. QFuture

2. QFutureIterator

3. QFutureWatcher

4. QFutureSynchronizer

세 가지 계산함수와 네 가지 결과출력자를 각각의 용도에 맞게 조합하여 사용 가능

## Map계열

- Map: N -> N

N개의 입력인자를 가진 배열의 각 인자에 대해 함수를 실행하고 N개의 출력인자를 가진 배열을 반환함

- Reduce: N -> M (단, M<=N)

특정한 결과배열(M개의 배열)에 N개의 인자를 가진 배열의 각 원소를 인자로 받는 함수를 N번 실행하고

M개의 결과배열을 반환

## Filter계열

- Filter: N -> M (단, M<=N)

N개의 입력인자를 가진 배열에 조건식을 적용 후 조건에 부합하는 M개의 출력인자를 가진 배열을 반환함

- Reduce: Map계열의 Reduce와 동일

## Run계열

가장 간단한 형태로 단일 함수를 즉시 실행

## QtConcurrent에서의 Map계열 함수

- QtConcurrent::map()

- QtConcurrent::mapped()

- QtConcurrent::mappedReduced()

## QtConcurrent에서의 Filter계열 함수

- QtConcurrent::filter()

- QtConcurrent::filtered()

- QtConcurrent::filteredReduced()

## QtConcurrent에서의 Run계열 함수

- QtConcurrent::run()

# QtConcurrent 사용 방법

QtConcurrent의 map, filter계열 함수는 lambda function을 지원 안함

참고 : https://stackoverflow.com/questions/43720869/make-qtconcurrentmapped-work-with-lambdas

> Unfortunately that QtConcurrent::mapped does not support lambda function with captures. You could need a custom implementation. 

따라서 map, filter, reduce함수를 외부에 따로 선언해줘야함

## map()과 mapped()의 차이

QtConcurrent::map()은 매 iteration에서 값을 반환하지 않으나 

QtConcurrent::mapped()는 매번 값을 반환함

이 각각의 결과를 QFutureWatcher의 resultReadyAt Signal을 통해 얻을 수 있음

map은 resultReadyAt이 어떠한 Signal도 발생시키지 않음

## mappedReduced() - Future - FutureWatcher - Pushbutton 연동 기본 예제

- 목표 : 1부터 100000000까지 실수를 제곱하여 더함

- mappedReduced는 Lambda Function과 호환되지 않으므로 map function과 reduce function을 정의해줘야함

- Array 선언부

```cpp
QList<double> list;
for(int i=1;i<100000001;i++) list.append(i);
```
   
- Map 선언부

```cpp
double mapFnc(const double& arrayData){
    return arrayData * arrayData;
}
```

- Reduce 선언부

```cpp
void reduceFnc(double& acc,const double& mappedData){
    result = result + mappedData;
}
```

- Future & FutureWatcher & Pushbutton 연결

```cpp
connect(startPush,&QPushButton::clicked,[=](){
    qDebug()<<"ON START PUSH";
    watcher = new QFutureWatcher<double>();
    QFuture<double> future = QtConcurrent::mappedReduced(list,mapFnc,reduceFnc);
    connect(watcher,SIGNAL(resultReadyAt(int)),this,SLOT(onResultReadyAt(int)));
    connect(watcher,SIGNAL(finished()),this,SLOT(onFinished()));
    watcher->setFuture(future);
});
```

## blockingMappedReduced와 QElapsedTimer를 이용한 시간 측정

일반 mappedReduced는 Future를 반환하나 blockingMappedReduced는 result를 반환

- Array, Map, Reduce : 상동

- 실행

```cpp
QElapsedTimer multiTimer;
multiTimer.start();
double multiResult = QtConcurrent::blockingMappedReduced(list,mapFnc,reduceFnc);
qDebug()<<"Result"<<multiResult;
qDebug()<<"ElapsedTimeMulti"<<multiTimer.elapsed();
```

- 일반 For와 비교

```cpp
QElapsedTimer singleTimer;
singleTimer.start();
QList<double> squaredList;
for(int i=0;i<list.size();i++){
  squaredList.append(list.at(i) * list.at(i));
}
double singleResult = 0.0;
for(int i=0;i<squaredList.size();i++){
  singleResult = singleResult + squaredList.at(i);
}
qDebug()<<"Result"<<singleResult;
qDebug()<<"ElapsedTimeSingle"<<singleTimer.elapsed();
```

# 계산 최적화

## Cumulative Sum of Vector

목표: [1,2,3,4,5,...] -> [1,3,6,10,15,...]

- Array: 상동

- std::partial_sum()을 이용

```cpp
qDebug()<<"Cum Sum Partial Start";
QElapsedTimer cumSumPartialTimer;
cumSumPartialTimer.start();
QVector<double> cumSumPartial(list.size());
std::partial_sum(list.begin(),list.end(),cumSumPartial.begin(),std::plus<double>());
qDebug()<<"CumsumPartial"<<cumSumPartialTimer.elapsed();
```

- for loop 이용

```cpp
qDebug()<<"Cum Sum Normal Start";
QElapsedTimer cumSumForTimer;
cumSumForTimer.start();
double temp=0.0;
int size = list.size();
QVector<double> cumSumFor(list.size());
for(int i=0;i<size;i++){
  temp+=list[i];
  cumSumFor[i]=temp;
}
qDebug()<<"cumSumFor"<<cumSumForTimer.elapsed();
```
