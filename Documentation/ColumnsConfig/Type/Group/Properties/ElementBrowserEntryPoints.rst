.. include:: /Includes.rst.txt
.. _columns-group-properties-elementBrowserEntryPoints:

==========================
elementBrowserEntryPoints
==========================

.. confval:: elementBrowserEntryPoints

   :Path: $GLOBALS['TCA'][$table]['columns'][$field]['config']
   :type: array
   :Scope: Display

   By default, the last selected page  is used when opening the element browser.
   Setting this configuration value changes this behaviour.

   This configuration value is a PHP :php:`array`, containing `table => id`
   pairs. When opening the element browser for a specific table (buttons below
   the group field), the defined page is then always selected by default. There
   is also the special `_default` key, used for the general element browser
   button (on the right side of the group field), which is not dedicated to a
   specific table.

   This configuration value also supports the known
   markers `###SITEROOT###`, `###CURRENT_PID###` and `###PAGE_TSCONFIG_<key>###`.

   Each `table => id` pair can also be overridden via page TSconfig.

Examples
========

Open the element browser on page 123 for tt_content elements
-------------------------------------------------------------

.. code-block:: php

    'simple_group' => [
        'label' => 'Simple group field',
        'config' => [
            'type' => 'group',
            'allowed' => 'tt_content',
            'elementBrowserEntryPoints' => [
                'tt_content' => 123,
            ]
        ]
    ],

This could then be overridden via page TSconfig:

.. code-block:: typoscript

    TCEFORM.my_table.simple_group.config.elementBrowserEntryPoints.tt_content = 321

Since only one table is allowed, the defined entry point is also automatically
used for the general element browser button.

Open the element browser on different pages for tt_content and news records
----------------------------------------------------------------------------
In case the group field allows more than one table, the `_default` key has to
be set:

.. code-block:: php

    'extended_group' => [
        'label' => 'Extended group field',
        'config' => [
            'type' => 'group',
            'allowed' => 'tt_content,tx_news_domain_model_news',
            'elementBrowserEntryPoints' => [
                '_default' => '###CURRENT_PID###' // E.g. use a special marker
                'tt_content' => 123,
                'tx_news_domain_model_news' => 124,
            ]
        ]
    ],

Of course, the `_default` key can also be overridden via page TSconfig:

.. code-block:: typoscript

    TCEFORM.my_table.extended_group.config.elementBrowserEntryPoints._default = 122
