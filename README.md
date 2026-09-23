# Create an SQL dump in the specified location

This GitHub action creates an SQL dump of the database using `drush` in a specified location. Then you can configure your project to work with [heavy-lifter](https://packagist.org/packages/eaudeweb/heavy-lifter) to retrieve the SQL dump and import in your local Drupal website installation.

## Usage

```yml
steps:

  - uses: eaudeweb/drupal-sql-dump-action@1.x
    with:
      ssh_user:           ${{ secrets.TEST_SSH_USER }}
      ssh_host:           ${{ secrets.TEST_SSH_HOST }}
      ssh_key:            ${{ secrets.TEST_SSH_KEY }}
      ssh_user_jumphost:    ${{ secrets.TEST_SSH_USER_JUMPHOST }}
      ssh_host_jumphost:    ${{ secrets.TEST_SSH_HOST_JUMPHOST }}
      sql_dump_file:      /var/www/config/www.example.com/sync/database.sql
      anonymize:          true
```

## SQL dump anonymization

The action can be configured to ask Drush to anonymize the SQL dump during the process, however the project itself must be configured properly to support anonymization.
Please refer to [gdpr-dump](https://github.com/eaudeweb/gdpr-dump) project to understand how first add support and configure in your Drupal project.