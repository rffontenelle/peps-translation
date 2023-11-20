PEPs translation
================

This project strives for the translation of Python Enhancement Proposals (PEP), and to publish them. 

For official info, see `PEP website`_ and its `GitHub repository`_.

Commands
~~~~~~~~

Update peps git submodule:

.. codeblock:: sh

    git -C peps checkout .
    git submodule init
    git submodule update
    git -C peps fetch origin
    git -C peps checkout main
    git -C peps reset --hard origin

Update translation files:

.. codeblock:: sh

    git -C peps apply ../enable-i18n.diff
    python peps/build.py --getext
    (cd peps && sphinx-intl update -d ../locales -p build/gettext)

Commit updated po files

.. codeblock:: sh

    git add locales/**/*.po
    git commit -m 'Update translation files'

PO files are now ready for translation. Use a offline translation editor software, like
`Poedit`_, `Gtranslator`_, or any other of your preference.

.. _PEP website: https://peps.python.org
.. _GitHub repository: https://github.com/python/peps
.. _Poedit: https://poedit.net
.. _Gtranslator: https://gitlab.gnome.org/GNOME/gtranslator/
