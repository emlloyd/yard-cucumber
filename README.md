Cucumber-In-The-YARD (CITY): A Requirements Documentation Tool
====================================

Synopsis
--------

Cucumber-In-The-Yard is a YARD extension that processes Cucumber features, scenarios, steps,
tags, step definitions, and even transforms to provide documentation similar to what you expect
to how YARD displays classes, methods and constants.  This tools bridges the gap of having 
feature files found in your source code and true documentation that your team, product owners
and stakeholders can use.

Examples
--------

I have created a trivial, example project to help provide a quick visualization of the resulting
documentation.  I encourage you to look at it as an example and see if it would assist your 
project from a multitude of perspectives: as the project's core developer; another developer or 
a new developer; quality assurance engineer; or product owner/stakeholder.

The implemented example has been deployed at [http://recursivegames.com/cukes/](http://recursivegames.com/cukes/).

**1. Formatted Features** [example](http://recursivegames.com/cukes/requirements/example/scenario.html)

**2. Search through features, scenarios, and tags** [example](http://recursivegames.com/cukes/feature_list.html) & [example](http://recursivegames.com/cukes/tag_list.html)

**4. View features and scenarios by tag** [example](http://recursivegames.com/cukes/requirements/tags/bvt.html)

**5. Steps link to their step definitions** [example](http://recursivegames.com/cukes/requirements/example/scenario.html)

**6. Step definitions show implemented steps** [example](http://recursivegames.com/cukes/requirements/step_transformers.html#definition_13-stepdefinition)

**7. Step definitions show the step transforms used** [example](http://recursivegames.com/cukes/requirements/step_transformers.html#transform_8-steptransform)

**8. Undefined steps are listed** [example](http://recursivegames.com/cukes/requirements/step_transformers.html#undefined_steps)

Installation
------------

Cucumber-In-The-Yard (CITY) requires the following gems installed:

    Gherkin - http://cukes.info
    Cucumber - http://cukes.info
    YARD - http://yardoc.org

To install CITY use the following command:

    $ gem install cucumber-in-the-yard
    
(Add `sudo` if you're installing under a POSIX system as root)

Usage
-----

**1. Rake Task**

You can do this by adding the following to your `Rakefile`:
    
    require "yard"
    require "city"

    YARD::Rake::CitydocTask.new do |t|
      t.files   = ['features/**/*', OTHER_PATHS]   # optional
      t.options = ['--any', '--extra', '--opts'] # optional
    end

both the `files` and `options` settings are optional. `files` will default to
`lib/**/*.rb` and `options` will represents any options you might want
to add. Again, a full list of options is available by typing `yardoc --help`
in a shell. You can also override the options at the Rake command-line with the
OPTS environment variable:

**2. YARD command-line**

    $ yardoc -e path/to/cucumber-in-the-yard/lib/city.rb -p path/to/cucumber-in-the-yard/lib/templates 'features/**/*.*'


Details
--------

There are two things that I enjoy: a test framework written in my own Domain Specific Language (DSL)
that is easily understood by all those on a project and the ability for all participants to easily read, 
search, and view the tests.

Cucumber is an amazing tool that allowed me to define exercisable requirements.  My biggest obstacle was
bringing these requirements to my team, the product owner, and other stakeholders.

Initially I tried to expose more of the functionality by providing freshly authored requirements through 
email, attachments to JIRA tickets, or linked in wiki documents.  None of these methods were very sustainable 
or successful.  First, I was continually pushing out the documents to those interested.  Second, the documents 
were displayed to the user in text without the syntax highlighting that was exceedingly 
helpful for quickly understanding the requirements.

I also found it hard to share the test framework that I had put together with another developer that joined 
the team.  It was difficult to direct them around the features, tags, step definitions, and transforms.  
It was when I started to convey to them the conventions that I had established that I wished I had a tool 
that would allow me to provide documentation like one would find generated by a great tool like YARD.

So I set out to integrate Cucumber objects like features, backgrounds, scenarios, tags, steps, step 
definitions, and transforms into a YARD template.  From my quick survey of the landscape I can see that the 
my needs are different than a lot of others that use Cucumber.  The entire project that spawned this effort 
was solely to exercise the functionality of a different, large project and so there is a huge dependence on
having the requirements documented.  This is in contrast to other projects that are using this on a small 
scale to test the functionality of small software component.  Though, ultimately, I realized that the 
functionality may provide a valuable tool for many as I feel it helps more solidly bridge the reporting of 
the documentation by putting a coat of paint on it.

Roadmap
-------

**Future Feature Ideas**

**1. Feature/Scenario Tag unions and intersections**

Create an AJAX interface that would allow the user to specify tags to union, intersect, or exclude to 
produce a list of features and scenarios that would execute.  The output could also provide an example
command line parameter list to produce the feature/scenario execution results.

Visualization of this execution with some graphing library for some extra points.

**2. Performance enhancements**

The current rate of documentation is not dreadfully slow anymore but more performance enhancements could
always be performed to produce the documentation faster.

**3. Requirements Only Docuementation**

'fulldoc' is the default documentation generated but I have this thought that a requirements-only document
may be useful.  Essentially the first draft would be the current documentation minus the class and method
links/searches and replacing the index.html.

**4. Before, After, and Around Hooks**

Document the additional before, after, and around hooks that Cucumber uses.  Specifically display the before, after, and around
hooks that are tied to tags (unions and intersections) on the tag pages.

**5. Layout refinements of the step definition / step tranform page**

More work could be done to make this page more searchable, sortable, and usable.

**6. Table Step Transforms**

The table step transform matching would be nice to show which tables are affected by table transforms



LICENSE
-------

(The MIT License)

Copyright (c) 2010 FIX

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
'Software'), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED 'AS IS', WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.