# Qt Creator 자동 코드 포매팅

https://doc.qt.io/qtcreator/creator-beautifier.html

- Astyle 다운로드

  윈도우 버젼 다운로드
  
http://astyle.sourceforge.net/

https://sourceforge.net/projects/astyle/files/astyle

- 세팅

1. Help - About Plugin - C++ - Beutifier 체크

2. 프로그램 재시작

3. Tool - Options - Beautifier - Artistic Style - Configuration에서 위에서 파일을 압축 풀고 /bin의 AStyle.exe 선택

> C:\Users\infomax\Downloads\AStyle_3.1_windows\AStyle\bin\AStyle.exe

4. Use specific config file로 모든 프로젝트를 공통으로 지정하거나 

   Use file \*.astylerc defined in project files로 프로젝트별로 지정

- 단축키 등록

  Tools - Options - Environment - Keyboard - ArtisticStyle - FormatFile을 선택 후 Shortcut에서 Record로 Alt + Shift + F 지정
  
  > Alt + Shift + F는 VSCode Prettier 플러그인의 디폴트 값이므로 동일하게 적용

- 예제 astyle 파일

  구글 스타일에서 space만 4로 변경
  
# google.astylerc
```
# 4 space indent
-s4
# Indent 'class' and 'struct' access modifiers, 'public:', 'protected:' and 'private:', one half indent.
-xG
# Indent 'switch' blocks so that the 'case X:' statements are indented in the switch block. The entire case block is indented.
-S
# Do not retain a backup of the original file. The original file is purged after it is formatted.
#-n
# Don't break one-line blocks.
-O
# Don't break complex statements and multiple statements residing on a single line.
-o
# Attach a pointer or reference operator (*, &, or ^) to the variable name (right).
-k3
# Insert space padding after paren headers only (e.g. 'if', 'for', 'while'...).
-H
# Insert space padding around operators.
-p
```
