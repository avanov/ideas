Plim DSL
===========

1. Assets management

       .. code-block:: plim

          require asset.name, asset.another.name
          require asset.one.more.name

2. Assets manager takes care of proper joining of files.

    Development environment

        .. code-block:: yaml

           - asset.name:
               - file1
               - file2
               - file3
           - asset.another.name:
               - file4
               - file5
               - file6

    Production environment

        .. code-block:: yaml

           - asset.name:
               - compiled_file1
           - asset.another.name:
               - compiled_file1

    In this case, the assets manager will get the idea that:

    1. file1..file6 should be compiled into a single file for production environment.
    2. ``require asset.name, asset.another.name`` will produce only one inclusion of the
       ``compiled_file1`` into a template.