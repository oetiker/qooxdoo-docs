Source Code Validation
======================

qooxdoo includes its own Javascript validator, **Ecmalint**, which application developers can use to check their source files for errors. It is started by running the *lint* generator job in an application directory:

    ./generate.py lint

Critical Warnings
-----------------

### Use of undefined or global identifier

This warning indicates that an unknown global variable is used. This can be caused by:

-   The variable is not declared as local variable using `var`
-   The variable name is misspelled
-   It is OK to use this global but EcmaLint does not know about it. This can be fixed by passing the variable name as known variable to the EcmaLint call or by adding a `@lint ignoreUndefined(VARIABLE_NAME)` doc comment to the method's API doc comment

### Unused identifier

### Map key redefined

### Data field has a reference value

**Hint:** If data fields are initialized in the members map with reference values like arrays or maps they will be shared between all instances of the class. Usually it is better to set the value to 'null' and initialize it in the constructor

### Use of deprecated identifier

Critical Warning (for framework)
--------------------------------

### Potentially non-local private data field

**Hint:** You should never do this.

### Protected data field

**Hint:** Protected data fields are deprecated. Better use private fields in combination with getter and setter methods.

**Comment:** It appears that this isn't an issue that is generically to be solved as the hint suggest. See the corresponding [bug report](http://bugzilla.qooxdoo.org/show_bug.cgi?id=2095).

### Undeclared private data field

**Hint:** You should list this field in the members section.

Coding Style Warnings
---------------------

### The statement of loops and conditions must be enclosed by a block in braces

### Multiply declared identifier

Explicitly ignoring messages
----------------------------

Here are some of the @ hints that can be used to explicitly suppress specific lint messages:

    @lint ignoreUnused(x, y)
    @lint ignoreDeprecated(alert)
    @lint ignoreUndefined(button1, foo)
    @lint ignoreReferenceField(field)

For a comprehensive list of possible @lint hints see the JSDoc reference \<pages/development/api\_jsdoc\_ref\#lint\>. Before lint prints a warning it walks up the AST and looks for the next enclosing API doc comment. Usually these comments should be placed in method JsDoc comments or in the class comment.

There are additional warning for which there is currently no key to suppress them as they are deemed too important (e.g. duplicate map keys). On the other hand, there might be additional checks to be wanting which are currently not implemented (e.g. checking protected fields).
