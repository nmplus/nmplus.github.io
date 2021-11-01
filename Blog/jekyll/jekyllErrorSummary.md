# debug

## 오류 발생 시 확인 방법
서버 실행 시 뒤에 --incremental 옵션을 붙여준다.
```
bundel exec jekyll serve --incremental
```

## 실행 시 오류 모음.

- `require': cannot load such file -- webrick (LoadError)
webrick이 없다는 것이므로 해당 모듈을 추가 해 준다
```
bundle add webrick
```
[참조 사이트](https://junho85.pe.kr/1850)


