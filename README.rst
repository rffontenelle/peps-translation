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

Prepare and enter the virtual environment:

.. codeblock:: sh

    make -C peps venv
    source peps/.venv/bin/activate

Update translation files:

.. codeblock:: sh
    
    sphinx-build -E -bgettext -Dgettext_compact=False -d peps/build/.doctrees peps/peps locales/pot
    sphinx-intl update --locale-dir locales

Commit updated po files

.. codeblock:: sh

    git add locales/**/*.po
    git commit -m 'Update translation files'

PO files are now ready for translation. Use a offline translation editor software, like
`Poedit`_, `Gtranslator`_, or any other of your preference.

Build documentation:

.. codeblock:: sh

    sphinx-build -bhtml -jauto -Dlanguage=pt_BR -Dlocale_dirs=locales/ -Dgettext_compact=False -Dgettext_auto_build=True -W --keep-going -w sphinx-warnings.txt peps/peps peps/build/html

.. _PEP website: https://peps.python.org
.. _GitHub repository: https://github.com/python/peps
.. _Poedit: https://poedit.net
.. _Gtranslator: https://gitlab.gnome.org/GNOME/gtranslator/
