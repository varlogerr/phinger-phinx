#Phinger MySQL

Collection of phing targets for Phinx migrations

## Installation

1) Run `composer require phinger/phinx`  
2) Add  
```
<property file="{path-to-lib}/phinx.yml" override="false" />
<import file="{path-to-lib}/phinx.xml" />
```
to your build file  
3) Create overrides configuration file and import it __before__ importing configuration from the library in order to override library properties.  
4) Run `phing -l` if you want to list all available targets  
5) Use library targets  

## Usage Demo

This demo will run migrations and seed database.  

_{project-path}/my-conf.yml_
```
# Only these 2 settings will be overriden. You can override any
# setting in the same way
phinger:
  phinx:
    environment: development
    config_path: ./my-bad-ass-migrations/phinx.yml
```

_{project-path}/build.xml_
```
<?xml version="1.0" encoding="UTF-8" ?>

<project
        name="test"
        default="setup-db"
>
    <property file="./my-conf.yml" />
    
    <property file="./vendor/phinger/phinx/phinx.yml" override="false" />
    <import file="./vendor/phinger/phinx/phinx.xml" />
    
    <target
            name="setup-db"
            depends="phinger:phinx:migrate,
                     phinger:phinx:seed"
    />
</project>
```
