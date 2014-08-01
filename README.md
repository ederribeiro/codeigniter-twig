# The Twig template library for CodeIgniter

## Installation

First download the [Twig library](http://twig.sensiolabs.org/), suggest via composer

    "require": {
        "twig/twig": "*"
    }

configure your composer.json vendors to install the libraries folder inside
    
    "config": {
        "vendor-dir": "application/libraries"
    }

Create twig cache directory under application/cache; and
give it write permission
	
    $ mkdir -p application/cache/twig
    $ chmod o+w application/cache/twig

Move the file /libraries/twig.php for the libraries folder of your project

Now, add the Twig config file to application/config/twig.php, customize it
    
    // Sets the name of template_dir that will be used with standard views_dir
    $config['template_dir'] = 'templates';
    // The standard views directory
    $config['views_dir'] = APPPATH.'views';
    // Sets the cache directory
    $config['cache_dir'] = APPPATH.'cache/twig';
    // Sets the file extensions that will be rendered
    $config['file_extension'] = '.html';

## Almost there...

Put in your controller,

    $this->load->library('twig'); // or you can load in the file config/autoload.php
    $data['title'] = "Testing Twig!!";
    
    // the first parameter you pass the name of your template, do not need to use the extension
    // the second parameter you can pass the name of the view to use, is optional
    // the third will be an array of variables that use the view and template
    $this->twig->display('template', 'view', $data);
    
## CodeIgniter helper functions

If you want to use CodeIgniter helper functions in Twig templates do this in
your controller.

    $this->load->library('twig'); // load the Twig library
    $this->load->helper('url'); // load the CodeIgniter URL helper
    // map the base_url() function as a Twig function 
    $this->twig->add_function('base_url'); 

Then in your Twig view call the base_url() function like this

    {{ base_url() }}

I hope to help you

## License

[MIT License](http://ederribeiro.mit-license.org/) Eder Ribeiro
