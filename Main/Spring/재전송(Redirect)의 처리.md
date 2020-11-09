# 재전송(Redirect)의 처리

### Sequence Diagram

http://plantuml.com/sequence-diagram

````uml
Alice -> Bob: Authentication Request
Bob --> Alice: Authentication Response

Alice -> Bob: Another authentication Request
Alice <-- Bob: another authentication Response
````

