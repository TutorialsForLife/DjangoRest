https://www.django-rest-framework.org/

Instalar a biblioteca de rest
```sh
pip install djangorestframework
pip install markdown       # Markdown support for the browsable API.
pip install django-filter  # Filtering support
```

Configurar no Settings do django
```python
INSTALLED_APPS = [
    ...
    'rest_framework',
]
```

O Django Rest Framework funciona com dois elementos básicos, são eles: Serializers e Views. O Serializer tem a ideia de preparar os dados vindos da model do django, como dados configurados para serem mostrados na API.

```python
from django.contrib.auth.models import MinhaModel
from rest_framework import serializers

class MinhaModelSerializer(serializers.HyperlinkedModelSerializer):
    class Meta:
        model = MinhaModel
        fields = ['nome', 'outrocampo', 'eoto']
```

Views são uma etapa de análise da requisição e organização da resposta. ViewSets são classes predefinidas com um conjunto de views. 


```python
from django.contrib.auth.models import User, Group
from rest_framework import viewsets
from tutorial.quickstart.serializers import UserSerializer, GroupSerializer


class UserViewSet(viewsets.ModelViewSet):
    """
    API endpoint that allows users to be viewed or edited.
    """
    queryset = User.objects.all().order_by('-date_joined')
    serializer_class = UserSerializer
```

```python
class UserViewSet(viewsets.ViewSet):
    """
    Example empty viewset demonstrating the standard
    actions that will be handled by a router class.

    If you're using format suffixes, make sure to also include
    the `format=None` keyword argument for each action.
    """

    def list(self, request):
        pass

    def create(self, request):
        pass

    def retrieve(self, request, pk=None):
        pass

    def update(self, request, pk=None):
        pass

    def partial_update(self, request, pk=None):
        pass

    def destroy(self, request, pk=None):
        pass
```
