module.dev
#  [Drupal 7 Module Development](https://www.safaribooksonline.com/library/view/drupal-7-module/9781849511162/)
### by Ken Rickard, John Wilkins, Larry Garfield, Matt Butcher, Greg Dunlap, Matt Farina
Publisher: Packt Publishing

Release Date: December 2010

ISBN: 9781849511162

Topics: Drupal

> ## Chapter 2. Creating Your First Module
### Creating new module

* Starting a new module
* Creating `.info` files to provide Drupal with module information
* Creating `.module` files to store Drupal code
* Adding new blocks using the **Block Subsystem**
* Using common Drupal functions
* Formatting code according to the Drupal coding standards
* Writing an automated test for Drupal

>__Our goal: a module with a block__

We are going to divide this task of building a new module into the three parts:

* Create a new module folder and module files
* Work with the Block Subsystem
* Write automated tests using the SimpleTest framework included in Drupal

#### Creating the module directory



__Writing the .info file__
> sites/all/module/__cusrom/first.info

__Note__
_Agile software development is a particular methodology designed to help teams of developers effectively and efficiently build software. While Drupal itself has not been developed using an agile process, it does facilitate many of the agile practices. To learn more about agile, visit http://agilemanifesto.org/ . This approach is called __Test-driven Development (TDD)__, and is a justly popular methodology._

__Note__
Drupal does not support INI-style section headers such as those found in the php.ini file._

__Tip__
_CVS is going away, and so is `$Id$`. While Drupal has been developed in __CVS__ from the early days through Drupal 7, it is now being migrated to a __Git__ repository. Git does not use `$Id$`, so it is likely that between the release of Drupal 7 and the release of Drupal 8, $Id$ tags will be removed._


__! Important__
 However, if one were to use, say, __closures__ (a feature introduced in PHP 5.3), then the following line would need to be added: `php 7.0.16`
 
__Note__
_JavaScript, CSS, image files, and PHP files (like templates) that do not contain functions that the module needs to know about needn't be included in `files[]` directives. The point of the directive is simply to indicate to Drupal that these files should be examined by Drupal._


__Note__
_Drupal does not contain a directive to indicate that another module is recommended or is optional. It is the task of the developer to appropriately document this fact and make it known. There is currently no recommended best practice to provide such information._

__Creating a module file__
> sites/all/module/__cusrom/first.module

__SOURCE CODE STANDARDS__
> http://drupal.org/coding-standards

__Indenting:__
_All PHP and JavaScript files use two spaces to indent. Tabs are never used for code formatting._

__Tip__
__Doc blocks in action: api.drupal.org__
_Drupal's doc blocks are used to generate the definitive source of Drupal API documentation at http://api.drupal.org._

Doc declaration
```
/**
* @file
* A module exemplifying Drupal coding practices and APIs.
*
* This module provides a block that lists all of the
* installed modules. It illustrates coding standards,
* practices, and API use for Drupal 7.
*/
```
Function declaration
```
/**
* Implements hook_help().
*/
```
__Implements hook_help().__
_Each hook has its own parameters, and all core Drupal hooks are documented at http://api.drupal.org._

_Drupal 8.2 [Events](https://api.drupal.org/api/drupal/core%21core.api.php/group/events/8.2.x) more >>> [The EventDispatcher Component](http://symfony.com/doc/current/components/event_dispatcher.html)_

__THE T() FUNCTION AND TRANSLATIONS__
_`t()` function is responsible for translating strings from one language into other._
* ! It cannot do anything with lines like this, though:
```
// Incorrect
$variable = 'This is a string';
t($variable);

// Correct
t('This is my string');
```
* The `t()` function should always be given a literal string for its first argument
* The t() function provides an alternate, and more secure, method for replacing placeholders in text with a value. 
```$xslt
// No Secure
print "Welcome, $username.";
```
_This code leaves open the possibility that the value of `$username` contains data that will break the HTML in the output — or worse, that it will open an avenue for a malicious user to inject JavaScript or other code into the output._
```
// Secureted
$values = array('@user' => $username);
print t('Welcome, @user', $values);
```
_If the placeholder begins with @, then before it inserts the value, Drupal sanitizes the value using its internal check_plain() function_

_If you are sure that the string doesn't contain any dangerous information, you can use a different symbol to begin your placeholder: the exclamation mark (!).
```$xslt
$values = array('!url' => 'http://example.com');
print t('The website can be found at !url', $values);
```
_Finally, there is a third placeholder decorator: the percent sign (%) tells Drupal to escape the code and to mark it as emphasized_
```$xslt
$values = array('%color' => 'blue');
print t('My favorite color is %color.', $values);
```
_printing of the string My favorite color is <em>blue</em>._

There are more things that can be done with t(), format_plural(), http://api.drupal.org/api/function/t/7

String Overrides module at http://drupal.org/project/stringoverrides

### Working with the Block API

__Note__
_[The entire Block API is documented in the official Drupal 7 API documentation, and even includes an example module:](http://api.drupal.org/api/drupal/developer--examples--block_example.module/7.)_

__The block info hook__

__The block view hook__




