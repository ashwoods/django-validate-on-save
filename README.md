Django Validate on Save
=======================

**Automatically call full_clean() on models during save() to prevent invalid data being saved.**

Surprisingly, this does not happen by default, apparently for
[backwards compatibility reasons][2].
    
**Author:** Francis Devereux, [Bright Interactive][1].

Adding to your Django Project
=============================

For Django 1.6, 1.5, 1.4 or 1.3:

Call `validate_on_save.validate_models_on_save('your_app_name')` from your
app's models.py (I put this call near the end of models.py, not sure whether
this matters).

For Django 1.7 or 1.8:

Create an `AppConfig` (https://docs.djangoproject.com/en/1.8/ref/applications/) and call `validate_on_save.validate_models_on_save('your_app_name')` in its `ready()` method.

Publishing releases to PyPI
===========================

To publish a new version of django-validate-on-save to PyPI, set the
`__version__` string in `validate_on_save/__init__.py`, then run:

    # Run the tests against multiple environments
    tox
	# Publish to PyPI
    ./setup.py publish
	# Tag (change 1.0.0 to the version you are publishing!)
	git tag -a v1.0.0 -m 'Version 1.0.0'
	git push --tags


Running the tests
=================

To run the tests against the current environment:

    ./manage.py test

To run the tests against multiple environments, install `tox` using
`pip install tox`, make sure you're not currently in a virtual environment,
then simply run `tox`:

    tox

Changelog
=========

1.1.4
-----
* Initial Python 3 support. Tox passes but I think that there is still work to do e.g. adding u prefix to strings.

1.1.3
-----
* No code changes - version number bump required because I uploaded a broken package of 1.1.2 to PyPI

1.1.2
-----
* Test against Django 1.8
* Avoid using deprecated django.db.models.loading on Django 1.7+

1.1.1
-----
* Don't load all the apps when setting the signals for the models to avoid a circular import

1.1.0
-----

* Add support for Django 1.7

1.0.0
-----

* Initial release

License
=======

Copyright (c) Bright Interactive Limited.
Started with django-reusable-app Copyright (c) DabApps.

All rights reserved.

Redistribution and use in source and binary forms, with or without 
modification, are permitted provided that the following conditions are met:

Redistributions of source code must retain the above copyright notice, this 
list of conditions and the following disclaimer.
Redistributions in binary form must reproduce the above copyright notice, this 
list of conditions and the following disclaimer in the documentation and/or 
other materials provided with the distribution.
THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND 
ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED 
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE 
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE 
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL 
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR 
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER 
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, 
OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE 
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

[1]: http://www.bright-interactive.com/
[2]: http://stackoverflow.com/questions/4441539/why-doesnt-djangos-model-save-call-full-clean
