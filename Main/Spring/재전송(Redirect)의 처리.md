# 재전송(Redirect)의 처리

게시글을 등록하는 과정에서 POST방식으로 데이터가 처리되는 과정을 UML로 표현 하면 다음과 같다.

![img](../../img/재전송(Redirect)의 처리/SoWkIImgAStDuN8goYylJYrIqBLJSCxFAodApyb9BR9IU3ElzVM2fQydp55uEtNjwrKhNqzUel1cGSlhxZLSC6KWJK1TO0D0MlHpCejBNY-Sen2Kcf9Pb9fSWirik4A5jpDslDas1wTf83iNpbLuspVZpTmjRvOtm6ntICrB0ReR0000.png)

Controller의 register() 메서드는 redirect:/list를 전송한다고 할때 브라우저는 이를 받은후 /list로 이동하게 된다.

만약 재전송(redirect:) 를 하지 않는다면 사용자는 브라우저의 새로고침을 이용해 동일한 내용을 계속 서버에 등록할 수 있는 문제가 발생할 수 있다.

CRUD의 C(등록),U(수정),D(삭제) 작업은 처리가 완료된 후에 동일 내용을 다시 전송할 수 없도로 아예 브라우저의 URL을 이동하는 방식을 이용한다.

이때 브라우저에서는 C(등록),U(수정),D(삭제) 작업의 처리결과를 바로 알 수 있도록 피드백을 주어야 하는데 모달창, 경고창등을 사용해서 처리해주게 된다.