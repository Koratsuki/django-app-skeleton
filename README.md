# django-app-skeleton

Skeleton APP in Django Framework
Just for testing purposes

# Stating

$ django-admin startproject skeleton
$ cd skeleton

$ mkdir apps
$ mkdir api
$ mkdir database
$ mkdir files
$ mkdir templates

$ cd apps
$ touch __init__.py
$ cd ..
$ cd api
$ touch __init__.py

$ mv skeleton config

# Change on manage.py:
os.environ.setdefault("DJANGO_SETTINGS_MODULE", "skeleton.settings")
# For:
os.environ.setdefault("DJANGO_SETTINGS_MODULE", "config.settings")

#On settings.py after the "import os" statement:

TPL_DIR = os.path.join(BASE_DIR, 'templates/')
DB_FILE = os.path.join(BASE_DIR, 'database/database.db')
CACHE_DIR = os.path.join(BASE_DIR, 'files/cache/')
MEDIA = os.path.join(BASE_DIR, 'files/media/')
STATIC = os.path.join(BASE_DIR, 'files/static/')
STATIC_FILES = os.path.join(BASE_DIR, 'files/static_files/')

ADMINS = (
('Admin', 'admin@admin.com'),
)

# Change this
ROOT_URLCONF = 'config.urls'

# Templates
TEMPLATES = [
{
'BACKEND': 'django.template.backends.django.DjangoTemplates',
'DIRS': [ TPL_DIR, ],
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

#WSGI statement:

WSGI_APPLICATION = 'config.wsgi.application'

# If we need cache
CACHES = {
'default': {
'BACKEND': 'django.core.cache.backends.filebased.FileBasedCache',
'LOCATION': CACHE_DIR,
'TIMEOUT': 60,
'OPTIONS': {
'MAX_ENTRIES': 1000
}
}
}

# Database
DATABASES = {
'default': {
'ENGINE': 'django.db.backends.sqlite3',
'NAME': DB_FILE,
}
}

# Use this to serve static files under '/static/'
STATICFILES_DIRS = (
os.path.join( STATIC ),
)

MEDIA_URL = '/media/'

MEDIA_ROOT = MEDIA

#django-admin collectstatic
#Collects the static files into STATIC_ROOT.
STATIC_ROOT = STATIC_FILES
