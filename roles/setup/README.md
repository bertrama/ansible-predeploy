# Purpose

This role sets up individual role variables from a much smaller 
set supplied to this role.

# Required Variables

If two or more sections require the same variable, it should be 
assumed that this is intentional.

## DB Role

* app_name
* deploy_users

## User Role

* app_name
* user_uid
* user_gid
* deploy_users

# Development

1. Create a file `tasks/<rolename>.yml`
2. Use the set_fact module to setup the variables.
3. Add a bare include line to `tasks/main.yml`
4. Note the variables that must be supplied to this role inside
   this readme, above.
   