# structure django 

## avant de commencer un projet django il faut :
* creer un nouveau dossier ex : dossier 1
* creer un environement virtuel a l'interieur de ce dossier
```python
python -m venv venv 
# OU
python3 -m venv venv 

```
* activer le :
```python
venv\Scripts\activate sur windows
# OU
source venv/bin/activate sur Mac ou linux 

```
* install django :
```python
 Run pip install django 

```
* creer encore un autre dossier a coter du venv ex : dossier 2


* a l'interieur de dossier 2 maintenant on creée notre projet 
```python
django-admin startproject nom du projet

```

* aussi il faut creer deux dossier dans dossier 2, static_cdn et media_cdn .

## bien passons maintenant a la configurations de notre projet 

* bien avant nous deuvons creer deux dossier templates et static dans notre projet 

* dans templates creer deux dossiers pages et bases 

* si vous avez bien suivie vous devez avoir cette structure :

```python
nom_du_projet/  
├─────────────── nom_du_projet_django/  
│                ├── __inti__.py
│                ├── settings.py
│                ├── urls.py
│                ├── wsgi.py
├─────────────── static/  
│                 ├
│                 ├
│                 ├ 
├─────────────── templates/  
│                ├── bases/  
│                │    ├
│                │    ├
│                ├── pages
│                │    ├── 
│                │    ├──
├─────────────── manage.py  .
```
## configurations de settings.py :
 * chercher une liste TEMPLATES a linterieur il y'a un dictionnaire chercher le nom DIRS et mettez templates dans sa liste comme ceci : 
 ```python
  TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': ["templates"],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
  ]
```
TOUT EN BAS APRES STATIC_URL = '/static/' METTEZ CECI  :
 ```python
  STATIC_URL = '/static/'
    STATICFILES_DIRS = [
        os.path.join(BASE_DIR, 'static')
    ]
    MEDIA_URL = '/media/'
    MEDIA_ROOT = os.path.join(BASE_DIR, '../media_cdn')
    STATIC_ROOT = os.path.join(BASE_DIR, '../static_cdn') 
```
## configurations de  urls.py :
 ```python
   from django.contrib import admin
    from django.urls import path,include
    from django.conf import settings
    from django.conf.urls.static import static

    urlpatterns = [
      path('admin/', admin.site.urls),
    ]

    if settings.DEBUG:
        urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
        urlpatterns += static(settings.STATIC_URL, document_root=settings.STATIC_ROOT)
```
## si tout est ok fait migrate :  ```python manage.py migrate   ```
## lance le server : ```python manage.py runserver   ```
## VOUS DEVEZ VOIR UNE FUSEZ ;)

