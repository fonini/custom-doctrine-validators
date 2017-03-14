# Custom doctrine validators #

A pack with some custom Doctrine validators, that helps with common validation tasks from brazilian programmers.


## Installation ##

### Via a Git clone

`git clone git://github.com/fonini/custom-doctrine-validators.git`

### Download the package

http://github.com/fonini/custom-doctrine-validators/zipball/master

Copy the files to the Validators dir. e.g: Doctrine/Validator

       
## Using the validators ##

### CEP

Validates a brazilian CEP. 
e.g.: 99150-000, 99.150-000, 99150000
    
````php
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
````

### CPF

Validates a brazilian CPF, applying an appropriate algoritm for this. Passing an extra parameter also validates the format of the string.
    
````php
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
            'cpf' => array('formatted' => true)
            )
        );
    }
}
````

### Phone number

Validates a brazilian phone number (including mobiles), with Anatel rules. e.g.: (54) 3342-0000. The regex used in this validator can be found here:
[Goncin's blog](http://goncin.wordpress.com/2010/08/30/validando-numeros-de-telefone-com-expressoes-regulares)
    
````php
// models/Customer.php

class Customer extends BaseCustomer
{
    // ...

    public function setTableDefinition(){
        parent::setTableDefinition();

        // Validate in any format
        $this->hasColumn('telefone', 'string', 9, array(
            'phone' => true
            )
        );
    }
}
````

### Brazilian states

Validates if the string is an brazilian state. 
e.g.: RS, SC, sp
    
````php
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
````

### URLs

Validates if the string is an valid URL. The URL can be a domain name or a IP address. A port is optional. The following
protocols are supported: http, https, ftp and ftps.
e.g.: http://www.fonini.net, ftp://10.1.1.1:21
    
````php
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
````

## Even numbers

Validates if the value is an even number.
e.g.: 2, 4, 10
    
````php
// models/Customer.php

class Customer extends BaseCustomer
{
    // ...

    public function setTableDefinition(){
        parent::setTableDefinition();

        // ...
        $this->hasColumn('number_of_wheels', 'integer', 2, array(
            'even' => true
            )
        );
    }
}
````

### Odd numbers

Validates if the value is an odd number.
e.g.: 3, 5, 9
    
````php
// models/Customer.php

class Customer extends BaseCustomer
{
    // ...

    public function setTableDefinition(){
        parent::setTableDefinition();

        // ...
        $this->hasColumn('odd_number', 'integer', 2, array(
            'odd' => true
            )
        );
    }
}
````


### Hexadecimal numbers

Validates if the value is a hexadecimal number
e.g.: ff0000, af4
    
````php
// models/Customer.php

class Customer extends BaseCustomer
{
    // ...

    public function setTableDefinition(){
        parent::setTableDefinition();

        // ...
        $this->hasColumn('hexa_code', 'string', 20, array(
            'hexnumber' => true
            )
        );
    }
}
````

### Alphanumeric values

Validates if the value is alphanumeric
e.g.: jonnas, a45fdw
    
````php
// models/Customer.php

class Customer extends BaseCustomer
{
    // ...

    public function setTableDefinition(){
        parent::setTableDefinition();

        // ...
        $this->hasColumn('alphanumeric_value', 'string', 50, array(
            'alphanumeric' => true
            )
        );
    }
}
````

### Brazilian money (Real)

Validates if the value is a valid amount of brazilian money (Real)
e.g.: 10,00, 50.400,65
    
````php
// models/Customer.php

class Customer extends BaseCustomer
{
    // ...

    public function setTableDefinition(){
        parent::setTableDefinition();

        // ...
        $this->hasColumn('price', 'string', 20, array(
            'brmoney' => true
            )
        );
    }
}
````

### Prime numbers

Validates if the value is a prime number.
e.g.: 1, 2, 3, 5, 13
    
````php
// models/Customer.php

class Customer extends BaseCustomer
{
    // ...

    public function setTableDefinition(){
        parent::setTableDefinition();

        // ...
        $this->hasColumn('prime_value', 'integer', 5, array(
            'primenumber' => true
            )
        );
    }
}
````

### Float point numbers

Validates if the value is a float point number
e.g.: 10.0, 230.90, 10
    
````php
// models/Customer.php

class Customer extends BaseCustomer
{
    // ...

    public function setTableDefinition(){
        parent::setTableDefinition();

        // ...
        $this->hasColumn('float_value', 'float', array(
            'floatpoint' => true
            )
        );
    }
}
````

### Palindrome

Validates if the value is a palindrome, a word that can be read the same way in either direction.
e.g.: arara, ana
    
````php
// models/Customer.php

class Customer extends BaseCustomer
{
    // ...

    public function setTableDefinition(){
        parent::setTableDefinition();

        // ...
        $this->hasColumn('word', 'string', 50, array(
            'palindrome' => true
            )
        );
    }
}
````

### Dollar

Validates if the value is a valid amount of dollars, with our without the sign.
e.g.: $1,234,567.89, 1234567.89, $0.00
    
````php
// models/Customer.php

class Customer extends BaseCustomer
{
    // ...

    public function setTableDefinition(){
        parent::setTableDefinition();

        // ...
        $this->hasColumn('price', 'string', 50, array(
            'dollar' => true
            )
        );
    }
}
````


## Questions, bugs, feature requests?

Send an e-mail to: jonnasfonini@gmail.com
