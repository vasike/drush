Drush can be run in your shell by typing `drush` from within your project root directory or anywhere within Drupal.

    $ drush [options] <command> [argument1] [argument2]

Use the [help command](commands/help.md) to get a list of available options and commands:

    $ drush help pm:list

For even more documentation, use the [topic command](commands/core_topic.md):

    $ drush topic

See the [installation documentation](install.md) for notes on setting up the `$PATH`.

Using the --uri option.
-----------

For multi-site installations, use a site alias or the --uri option to target a particular site.

    $ drush --uri=http://example.com pm:install

Site Aliases
------------

Drush lets you run commands on a remote server. Once defined, aliases can be referenced with the @ nomenclature, i.e.

```bash
# Run pending updates on staging site.
$ drush @staging updatedb
# Synchronize staging files to production
$ drush rsync @staging:%files/ @live:%files
# Synchronize database from production to local, excluding the cache table
$ drush sql:sync --structure-tables-key=custom @live @self
```

See [Site aliases](site-aliases.md) for more information.

XDebug
------

If you are using XDebug, it is recommended to put `./vendor/drush/drush/bin` in your `$PATH` instead of `./vendor/bin`. If you use this alternate `drush` script, then Xdebug will be disabled by default. This improves performance substantially, because developers are often debugging something other than Drush and they still need to clear caches, import config, etc. There are two equivalent ways to override Drush's disabling of Xdebug:

- Pass the `--xdebug` global option.
- Set an environment variable: `DRUSH_ALLOW_XDEBUG=1 drush [command]`

If you are using the php `drush` script in `vendor/bin`, you can manually disable XDebug via an environment variable:
```
export XDEBUG_MODE=off
```
