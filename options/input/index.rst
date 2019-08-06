.. _input-options:

#######################
Input Processor Options
#######################

.. toctree::
   :maxdepth: 1

   tex
   mathml
   asciimath

-----

.. _input-common-options:

Options Common to All Input Processors
======================================

The following options are common to all the input processors listed
above.  They are given here with their default values, using the
``tex`` block as an example.

.. code-block:: javascript

    MathJax = {
      tex: {
        skipTags: [                       //  HTML tags that won't be searched for math
            'script', 'noscript', 'style', 'textarea', 'pre',
            'code', 'annotation', 'annotation-xml'
        ],
        includeTags: {                    //  HTML tags that can appear within math
            br: '\n', wbr: '', '#comment': ''
        },
        ignoreClass: 'tex2jax_ignore',    //  class that marks tags not to search
        processClass: 'tex2jax_process'   //  class that marks tags that should be searched
      }
    };

-----


Option Descriptions
===================

.. raw:: html

   <style>
   .rst-content dl.describe > dt:first-child {
     margin-bottom: 0;
   }
   .rst-content dl.describe > dt + dt {
     margin-top: 0;
     border-top: none;
     padding-left: 4.5em;
   }
   .rst-content dl.describe > dt + dd {
     margin-top: 6px;
   }
   </style>


.. describe:: skipTags: ['script', 'noscript', 'style', 'textarea',
                         'pre', 'code', 'annotation', 'annotation-xml']

    This array lists the names of the tags whose contents should not
    be processed by MathJaX (other than to look for ignore/process
    classes as listed below).  You can add to (or remove from) this
    list to prevent MathJax from processing mathematics in specific
    contexts.  E.g.,

    .. code-block:: javascript

       skipTags: {'[-]': ['code', 'pre'], '[+]': ['li']}

    would remove ``'code'`` and ``'pre'`` tags from the list, while
    adding ``'li'`` tags to the list.

.. describe:: includeTags: {br: '\n', wbr: '', '#comment': ''}

   This object specifies what tags can appear within a math
   expression, and what text to replace them by within the math.  The
   default is to allow ``<br>``, which becomes a newline, and ``<wbr>``
   and HTML comments, which are removed entirely.

.. describe:: ignoreClass: 'tex2jax_ignore'

    This is the class name used to mark elements whose contents should
    not be processed by MathJax (other than to look for the
    ``processClass`` pattern below).  Note that this is a regular
    expression, and so you need to be sure to quote any `regexp`
    special characters.  The pattern is inserted into one that
    requires your pattern to match a complete word, so setting
    ``ignoreClass: 'class2'`` would cause it to match an element with
    ``class='class1 class2 class3'`` but not ``class='myclass2'``.
    Note that you can assign several classes by separating them by the
    vertical line character (``|``).  For instance, with
    ``ignoreClass: 'class1|class2'`` any element assigned a class of
    either ``class1`` or ``class2`` will be skipped.  This could also
    be specified by ``ignoreClass: 'class[12]'``, which matches
    ``class`` followed by either a ``1`` or a ``2``.

.. describe:: processClass: 'tex2jax_process'

    This is the class name used to mark elements whose contents
    *should* be processed by MathJax.  This is used to restart
    processing within tags that have been marked as ignored via the
    ``ignoreClass`` or to cause a tag that appears in the ``skipTags``
    list to be processed rather than skipped.  Note that this is a
    regular expression, and so you need to be sure to quote any
    `regexp` special characters.  The pattern is inserted into one
    that requires your pattern to match a complete word, so setting
    ``processClass: 'class2'`` would cause it to match an element with
    ``class='class1 class2 class3'`` but not ``class='myclass2'``.
    Note that you can assign several classes by separating them by the
    vertical line character (``|``).  For instance, with
    ``processClass: 'class1|class2'`` any element assigned a class of
    either ``class1`` or ``class2`` will have its contents processed.
    This could also be specified by ``ignoreClass: 'class[12]'``,
    which matches ``class`` followed by either a ``1`` or a ``2``.

|-----|
