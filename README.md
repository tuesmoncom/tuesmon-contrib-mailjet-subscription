Tuesmon Contrib MailJet Subscription
=====================================

![Kaleidos Project](http://kaleidos.net/static/img/badge.png "Kaleidos Project")
[![Managed with Tuesmon.com](https://manage.tuesmon.com/support/images/tuesmon-badge-gh.png)](https://tuesmon.com "Managed with Tuesmon.com")

Plugin to subscribe and unsubscribe users to the newsletter list in MailJet


Installation
------------

**NOTE:** *Remeber that you need to create a contact list in MailJet and create the contact properties `username` (string), `full_name` (string) and `is_tuesmon_user` (boolean).*

### Production env

#### Tuesmon Back

In your Tuesmon back python virtualenv install the pip package `tuesmon-contrib-mailjet-subscription` with:

```bash
  pip install -e "git+https://github.com/tuesmoncom/tuesmon-contrib-mailjet-subscription.git@stable#egg=tuesmon-contrib-mailjet-subscription&subdirectory=back"
```

Then modify in `tuesmon-back` your `settings/local.py` and include this line:

```python
  MAILJET_API_KEY = "XXXXXXXXXXXXXXXXX"
  MAILJET_SECRET_KEY = "XXXXXXXXXXXXXXXXX"
  MAILJET_CONTACTLIST_ID = "my-contactlist-id"

  INSTALLED_APPS += ["tuesmon_contrib_mailjet_subscription"]
```


#### Tuesmon Front

Download in your `dist/plugins/` directory of Tuesmon front the `tuesmon-contrib-mailjet-subscription` compiled code (you need subversion in your system):

```bash
  cd dist/
  mkdir -p plugins
  cd plugins
  svn export "https://github.com/tuesmoncom/tuesmon-contrib-mailjet-subscription/branches/stable/front/dist" "mailjet-subscription"
```

Include in your `dist/conf.json` in the `contribPlugins` list the value `"/plugins/mailjet-subscription/mailjet-subscription.json"`:

```json
...
    "contribPlugins": [
        (...)
        "/plugins/mailjet-subscription/mailjet-subscription.json"
    ]
...
```


### Dev env

#### Tuesmon Back

Clone the repo and

```bash
  cd tuesmon-contrib-mailjet-subscription/back
  workon tuesmon
  pip install -e .
```

Then modify in `tuesmon-back` your `settings/local.py` and include this line:

```python
  MAILJET_API_KEY = "XXXXXXXXXXXXXXXXX"
  MAILJET_SECRET_KEY = "XXXXXXXXXXXXXXXXX"
  MAILJET_CONTACTLIST_ID = "my-contactlist-id"

  INSTALLED_APPS += ["tuesmon_contrib_mailjet_subscription"]
```


#### Tuesmon Front

After clone the repo link `dist` in `tuesmon-front` plugins directory:

```bash
  cd tuesmon-front/dist
  mkdir -p plugins
  cd plugins
  ln -s ../../../tuesmon-contrib-mailjet-subscription/front/dist mailjet-subscription
```

Include in your `dist/conf.json` in the `contribPlugins` list the value `"/plugins/mailjet-subscription/mailjet-subscription.json"`:

```json
...
    "contribPlugins": [
        (...)
        "/plugins/mailjet-subscription/mailjet-subscription.json"
    ]
...
```

In the plugin source dir `tuesmon-contrib-mailjet-subscription` run

```bash
npm install
```
and use:

- `gulp` to regenerate the source and watch for changes.
- `gulp build` to only regenerate the source.
