## [1] Create
### 1. Create
- 코드
```python
# articles/urls.py
from django.contrib.urls import path
from . import views
app_name = 'accounts'
urlpatterns = [
    path('', views.index, name='index'),
]
```
