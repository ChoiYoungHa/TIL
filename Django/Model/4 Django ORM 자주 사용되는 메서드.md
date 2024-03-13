# 4.Django ORM 자주 사용되는

장고에서 데이터를 조회할 때 자주 사용되는 메서드를 정리해 봤습니다.

### 자주 사용되는 메서드와 예제

**`exact`**: 지정된 값과 정확히 일치하는 항목을 찾습니다. 이는 기본 룩업 타입이므로, 대부분의 경우 필드명만 지정해도 `exact` 룩업이 적용됩니다.

```python
# name이 'John Doe'인 환자 찾기
patients = Patient.objects.filter(name__exact='John Doe')
# 또는 단순히
patients = Patient.objects.filter(name='John Doe')

```

**`iexact`**: 대소문자를 구분하지 않고 지정된 값과 정확히 일치하는 항목을 찾습니다.

```python
# name이 'john doe' (대소문자 구분 없음)인 환자 찾기
patients = Patient.objects.filter(name__iexact='john doe')

```

**`contains`**: 지정된 값을 포함하는 항목을 찾습니다. 대소문자를 구분합니다.

```python
# name에 'Doe'를 포함하는 환자 찾기
patients = Patient.objects.filter(name__contains='Doe')

```

**`icontains`**: 지정된 값을 포함하는 항목을 찾습니다. 대소문자를 구분하지 않습니다.

```python
# name에 'doe'를 포함하는 환자 찾기 (대소문자 구분 없음)
patients = Patient.objects.filter(name__icontains='doe')

```

**`gt`, `gte`, `lt`, `lte`**: 각각 '보다 큰(greater than)', '보다 크거나 같은(greater than or equal to)', '보다 작은(less than)', '보다 작거나 같은(less than or equal to)' 조건을 적용합니다.

```python
# 나이가 30보다 큰 환자 찾기
patients = Patient.objects.filter(age__gt=30)

# 나이가 20보다 작거나 같은 환자 찾기
patients = Patient.objects.filter(age__lte=20)

```

**`startswith`와 `endswith`**: 필드 값이 지정된 문자열로 시작하거나 끝나는 항목을 찾습니다. 대소문자를 구분합니다.

```python
# 이름이 'John'으로 시작하는 환자 찾기
patients = Patient.objects.filter(name__startswith='John')

# 이름이 'Doe'로 끝나는 환자 찾기
patients = Patient.objects.filter(name__endswith='Doe')

```

**`istartswith`와 `iendswith`**: `startswith`와 `endswith`와 유사하지만, 대소문자를 구분하지 않습니다.

```python
# 이름이 'john'으로 시작하는 환자 찾기 (대소문자 구분 없음)
patients = Patient.objects.filter(name__istartswith='john')

```

### 필터링 및 정렬 메서드

**`range`**: 지정된 두 값 사이에 있는 항목을 찾습니다. 이 룩업은 날짜 범위 조회나 수치 범위 조회에 유용하게 사용됩니다.

```python
from datetime import date

# 2020년 1월 1일부터 2020년 12월 31일 사이에 등록된 환자 찾기
start_date = date(2020, 1, 1)
end_date = date(2020, 12, 31)
patients = Patient.objects.filter(registration_date__range=(start_date, end_date))

```

**`date`, `year`, `month`, `day`, `week_day`**: 날짜 필드에 대한 특정 날짜, 연도, 월, 일, 요일을 기준으로 항목을 찾습니다. 이들 룩업은 날짜 필드에 대한 정밀한 쿼리를 가능하게 합니다.

```python
# 2020년에 등록된 환자 찾기
patients = Patient.objects.filter(registration_date__year=2020)

# 매주 월요일에 등록된 환자 찾기 (Django에서 일요일=1, 월요일=2)
patients = Patient.objects.filter(registration_date__week_day=2)

```

**`isnull`**: 필드 값이 `NULL`인지 아닌지를 기준으로 항목을 찾습니다. 이 룩업은 선택적 필드가 비어있는 객체를 찾을 때 유용합니다.

```python
# 전화번호가 등록되지 않은 환자 찾기
patients = Patient.objects.filter(phone_number__isnull=True)

```

**`in`**: 주어진 리스트나 쿼리셋에 포함된 값들 중 하나와 일치하는 항목을 찾습니다. 이 룩업은 여러 가능한 값 중에서 선택해야 할 때 유용합니다.

```python
# 특정 ID 리스트에 해당하는 환자 찾기
patient_ids = [1, 2, 3, 4]
patients = Patient.objects.filter(id__in=patient_ids)

```

이처럼, Django의 다양한 룩업 메서드들은 데이터를 효과적으로 조회하고 필터링하는 데 큰 도움을 줍니다. 이 기능들을 활용하여 보다 정교하고 효율적인 데이터 접근 방식을 구현할 수 있으며, 애플리케이션의 데이터 처리 능력을 대폭 향상시킬 수 있습니다.

이러한 룩업 메서드들은 Django에서 데이터베이스 쿼리를 간결하고 표현력 있게 작성할 수 있게 해줍니다. 각 룩업 메서드는 특정 필드와 값에 대한 조건을 정의하는 데 사용되며, 데이터 조회 과정을 매우 유연하게 만들어 줍니다.