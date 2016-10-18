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
