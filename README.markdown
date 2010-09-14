# Custom doctrine validators #

A pack with some custom Doctrine validators, that helps with common validation tasks from brazilian programmers.


## Installation ##

  * Via a Git clone

        git clone git://github.com/fonini/custom-doctrine-validators.git

  * Download the package

        [http://github.com/fonini/custom-doctrine-validators/zipball/master](http://github.com/fonini/custom-doctrine-validators/zipball/master)

  * Copy the files to the Validators dir. e.g: Doctrine/Validator

       
## Using the validators ##

* CEP

Validates a brazilian CEP. e.g.: 99150-000, 99.150-000, 99150000
    
    [php]
    // models/Customer.php

    class Customer extends BaseCustomer
    {
       // ...

	   public function setTableDefinition(){
		   parent::setTableDefinition();

		   // ...

		   $this->hasColumn('cep', 'string', 9, array(
				'cep' => true
			   )
		   );
	   }
   }


* CPF

Validates a brazilian CPF, applying an appropriate algoritm for this. Passing an extra parameter also validates the format of the string.
    
    [php]
    // models/Customer.php

    class Customer extends BaseCustomer
    {
       // ...

	   public function setTableDefinition(){
		   parent::setTableDefinition();

		   // ...
           // Validate in any format
		   $this->hasColumn('cpf_in_any_format', 'string', 14, array(
				'cpf' => true
			   )
		   );

           // Validate only formatted CPF's
		   $this->hasColumn('cpf_formatted', 'string', 14, array(
				'cpf' => array('formatted => true)
			   )
		   );
	   }
   }


* Phone number

Validates a brazilian phone number (including mobiles), with Anatel rules. e.g.: (54) 3342-0000. The regex used in this validator can be found her
[Goncin's blog](http://goncin.wordpress.com/2010/08/30/validando-numeros-de-telefone-com-expressoes-regulares).
    
    [php]
    // models/Customer.php

    class Customer extends BaseCustomer
    {
       // ...

	   public function setTableDefinition(){
		   parent::setTableDefinition();

		   // ...
           // Validate in any format
		   $this->hasColumn('telefone', 'string', 9, array(
				'telefone' => true
			   )
		   );
	   }
   }


* Brazilian states

Validates if the string is an brazilian state. 
i.e.: RS, SC, sp
    
    [php]
    // models/Customer.php

    class Customer extends BaseCustomer
    {
       // ...

	   public function setTableDefinition(){
		   parent::setTableDefinition();

		   // ...
		   $this->hasColumn('estado', 'string', 2, array(
				'brstate' => true
			   )
		   );
	   }
   }


* URL's

Validates if the string is an valid URL. The URL can be a domain name or a IP address. A port is optional. The following
protocols are supported: http, https, ftp and ftps.
i.e.: http://www.fonini.net, ftp://10.1.1.1:21
    
    [php]
    // models/Customer.php

    class Customer extends BaseCustomer
    {
       // ...

	   public function setTableDefinition(){
		   parent::setTableDefinition();

		   // ...
		   $this->hasColumn('url', 'string', 2, array(
				'url' => true
			   )
		   );
	   }
   }


## Questions, bugs, feature requests? ##

Send an e-mail to: contato@fonini.net
