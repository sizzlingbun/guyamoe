# Guya.moe
Generalized manga reading framework. Adapted for Kaguya-sama manga, but can be used generically for any and all manga.

Testing Supported By<br/>
<img width="160" src="http://foundation.zurb.com/sites/docs/assets/img/logos/browser-stack.svg" alt="BrowserStack"/>

## Prerequisites 

- Python 3.6.5+
  
## Install

`pip install -r requirements.txt`

In the `settings.py` file in the `guyamoe` folder, edit the `SECRET_KEY` with a randomly generated string to be used for hashing. e.g. `SECRET_KEY = 's2&_ky$%ib6x5h4kqtj&izm%t+a2)iq(755c-f&uot3$1mde7-'`

In command line/terminal, run:
-  `./manage.py makemigrations`
-  `./manage.py migrate`
-  `./manage.py loaddata reader/fixtures/reader_data.json`
-  `./manage.py createsuperuser` - prompts to create login

Before starting the server, create a `media` folder in the base directory. Add manga with the corresponding chapters and page images. Structure it like so:
```
media
└───manga
    └───<series-slug-name>
        └───001
            ├───001.jpg
            ├───002.jpg
            └───...
```
E.g. `Kaguya-Wants-To-Be-Confessed-To` for `<series-slug-name>`. 

Note: Zero pad chapter folder numbers like so: `001` for the Kaguya series (this is how the fixtures data for the series has it). It doesn't matter for pages though nor does it have to be .jpg. Only thing required for pages is that the ordering can be known from a simple numerical/alphabetical sort on the directory.

## Start the server

-  `./manage.py runserver` - keep this console active

Now the site should be accessible on localhost:8000

## Other info

Relevant urls (as of now): 

- `/` - home page
- `/about` - about page
- `/admin` - admin view (login with created user above)
- `/reader/series/<series_slug_name>` - series info and all chapter links
- `/reader/series/<series_slug_name>/<chapter_number>/<page_number>` - url scheme for reader opened on specfied page of chapter of series.
- `/api/series/<series_slug_name>` - all series data requested by reader frontend
- `/media/manga/<series_slug_name>/<chapter_number>/<page_file_name>` - url scheme to used by reader to actual page as an image.

