========
doitlive
========

`doitlive` is a tool for live presentations in the terminal. It reads a file of shell commands and replays the commands in a fake terminal session as you type random characters.

This project is a fork of `sloria/doitlive`_ aiming at introducing experimental support for markdown-based rendering of comments. If you are not after the markdown support introduced by this fork you should use the upstream project instead.


Get it now
----------

.. code-block:: bash

    $ pip install git+https://github.com/avicent/doitlive.git

Requires Python >= 2.7 or >= 3.3 with pip.

Differences with respect to `sloria/doitlive`_
-----------------------------------------------

The following magic-comments/directives are supported:

- ``#doitlive commentformat: [markdown|plain]``
    - Tells `doitlive` to interpret the comments as markdown-encoded and, provided ``commentecho`` is on, to render them using ``mdv`` (see Dependecies below). Note that the leading the hash character and the first space are stripped from the original line before rendering them as markdown.
- ``#doitlive markdowntheme: <theme>``
    - Tells `doitlive` to force ``mdv`` into using the specified theme for both text and code. Run ``mdv -it all`` to see theme samples.
- ``#doitlive click: <method>``
    - Instructs `doitlive` to call ``click.<method>()``. This can be useful to pause after echoing some of the comments.
- ``#doitlive cd: <path>``
    - Tells `doitlive` to quietly change the directory.

In addition, a line starting with at least eight ``#`` signs will be treated as section divider and will result in a prompt to press any key to continue at the bottom of the screen prior to having the screen cleaned.

Example
-------

.. code-block:: bash

    #doitlive shell: /bin/bash
    #doitlive prompt: default
    #doitlive commentecho: true
    #doitlive speed: 1000
    #doitlive commentformat: markdown
    #doitlive markdowntheme: 884.0134
    
    # # DEMONSTRATING DOITLIVE (1/2)
    #
    # This comment is interpreted as markdown. We can use:
    #
    # - Bullet lists.
    # - Syntax _highlighting_.
    # - Horizontal separators, as the one below.
    #
    # ---
    whatis windows
    
    ################################################
    # # DEMONSTRATING DOITLIVE (2/2)
    #
    # We can also use `#doitlive click: getchar` to insert pauses.
    
    #doitlive click: getchar
    # Now we continue after the pause.
    #
    # ---
    echo "That's all folks!"

Dependencies
------------

This fork introduces the following dependencies on top of the upstream ones:

- ``mdv``
    - Used for rendering the markdown comments to the terminal .  Note that the dependency to ``mdv`` in ``setup.py`` is pointing to `avicent/mdv`_ and not the original ``mdv`` from `axiros/mdv`_ in order to improve some rendering aesthetics. The official ``mdv`` should also work, though.
- ``blessed``
    - Used for positioning the cursor.

More information
----------------

- https://doitlive.readthedocs.io

Kudos
-----

- `sloria/doitlive`_

License
-------

MIT licensed. See the bundled `LICENSE <https://github.com/avicent/doitlive/blob/master/LICENSE>`_ file for more details.

.. _`sloria/doitlive`: https://github.com/sloria/doitlive
.. _`avicent/mdv`: https://github.com/avicent/terminal_markdown_viewer
.. _`axiros/mdv`: https://github.com/axiros/terminal_markdown_viewer
