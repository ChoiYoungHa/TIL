# 3.Django ORM 데이터 저장

Django의 ORM(Object-Relational Mapping)은 데이터베이스 작업을 추상화하여 Python 코드를 통해 데이터베이스를 조작할 수 있게 해준다. `Patient.objects.create()`, `save()`, `bulk_create()`와 같은 메서드는 데이터 삽입 작업을 수행하는 데 사용 됨.

🐍: **1. `Patient.objects.create()`**

- `create()` 메서드는 `Patient` 모델의 새 인스턴스를 생성하고, 이를 데이터베이스에 즉시 저장합니다. 이 메서드는 모델 필드를 인자로 받아서, 해당 인자들을 사용하여 데이터베이스에 새로운 레코드를 생성한다. `create()`는 모델 인스턴스를 만들고, 해당 인스턴스에 대해 `save()` 메서드를 내부적으로 호출하는 과정을 한 번에 처리 함.

```python
patient = Patient.objects.create(name="John Doe", age=30)

```

위 코드는 `name`과 `age` 필드를 가진 `Patient` 모델의 새 인스턴스를 생성하고, 이를 데이터베이스에 저장합니다.

**2. `save()` 메서드**

- `save()` 메서드는 모델 인스턴스를 데이터베이스에 저장하거나 업데이트 한다. `create()` 메서드와 달리, `save()`는 이미 존재하는 인스턴스에 대한 변경 사항을 저장할 때도 사용 된다. 즉, 인스턴스를 처음 만들 때는 새 레코드를 데이터베이스에 추가하고, 이미 존재하는 인스턴스를 수정한 후 `save()`를 호출하면 해당 레코드를 업데이트

```python
patient = Patient(name="Jane Doe", age=28)
patient.save()  # 새 레코드를 데이터베이스에 저장

```

**3. `bulk_create()` 메서드**

- `bulk_create()` 메서드는 데이터베이스에 대량의 레코드를 한 번에 삽입하는 데 사용된다. 이 메서드는 모델 인스턴스의 리스트를 인자로 받아, 이를 데이터베이스에 효율적으로 삽입합니다. `bulk_create()`는 대량의 데이터를 빠르게 삽입해야 할 때 유용하며, 개별적으로 `save()`를 호출하는 것보다 성능 측면에서 우수 함.

```python
patients = [
    Patient(name="John Doe", age=30),
    Patient(name="Jane Doe", age=28),
]
Patient.objects.bulk_create(patients)

```

위 코드는 여러 `Patient` 인스턴스를 한 번에 데이터베이스에 삽입한다.