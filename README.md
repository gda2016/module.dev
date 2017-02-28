module.dev
# [Drupal 7 Module Development] (https://www.safaribooksonline.com/library/view/drupal-7-module/9781849511162/)
## by Ken Rickard, John Wilkins, Larry Garfield, Matt Butcher, Greg Dunlap, Matt Farina
Publisher: Packt Publishing

Release Date: December 2010

ISBN: 9781849511162

Topics: Drupal

> ## Chapter 2. Creating Your First Module

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