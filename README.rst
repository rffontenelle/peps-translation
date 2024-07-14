PEPs translation
================

This project strives for the translation of Python Enhancement Proposals (PEP), and to publish them. 

For official info, see `PEP website`_ and its `GitHub repository`_.

Commands
~~~~~~~~

Update peps git submodule:

.. codeblock:: sh

    git -C peps checkout .
    git submodule update --init --remote

Prepare and enter the virtual environment:

.. codeblock:: sh

    make -C peps venv
    source peps/.venv/bin/activate
    pip install sphinx-intl

Update translation files:

.. codeblock:: sh
    
    sphinx-build -E -bgettext -Dgettext_compact=0 -d peps/build/.doctrees-gettext peps/peps locales/pot
    sphinx-intl update --locale-dir locales

Commit updated po files

.. codeblock:: sh

    git add locales/**/*.po
    git commit -m 'Update translation files'

PO files are now ready for translation. Use a offline translation editor software, like
`Poedit`_, `Gtranslator`_, or any other of your preference.

Build documentation (replace 'pt_BR' with the desired language):

.. codeblock:: sh

    make -C peps html SPHINXOPTS='-Dgettext_auto_build=True -Dgettext_compact=0 -Dlocale_dirs=../../locales -Dlanguage=pt_BR'

.. _PEP website: https://peps.python.org
.. _GitHub repository: https://github.com/python/peps
.. _Poedit: https://poedit.net
.. _Gtranslator: https://gitlab.gnome.org/GNOME/gtranslator/
