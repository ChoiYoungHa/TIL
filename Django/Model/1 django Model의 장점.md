# 1.django Model의 장점

jango의 모델은 파이썬 코드로 DB와 상호작용할 수 있는 SQL문으로 바꿔준다.

```python
from django.db import models

class Person(models.Model):
	first_name = models.CharField(max_length=30)
	last_name = models.CharField(max_length=30)
	

```

변경

```python
CREATE TABLE myapp_person(
	"id" serial NOT NULL PRIMARY KEY,
	"first_name" varchar(30) NOT NULL,
);
```

파이썬 코드만 신경써 주어도 DB와 상호작용이 가능하다.