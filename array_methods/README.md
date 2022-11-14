# Array Methods
Often in computing, our programs are repeating the same operation
in a sequence or over a data set.
This is such a common task that programming languages will define a variery
of ways to acomplish this.
Imperative languages will provide looping constructs such as `for` and `while`
where iteration is controlled manually by the programmer.
Functional languages provide *array methods* where the programmer defines
the operation they want to perform over data
and the language applies it to each data point.

Javascript gives programmers both options.
In this chapter we will go into detail about the array methods,
particularly
[`map`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/map),
[`filter`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter), and
[`reduce`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce).

Array methods are at the heart of functional programming and some of the
approaches we discuss here will set us up for some more advanced functional
patterns.

## Spreadsheet Analogy
Data manipulation is such a core task that speicialised tools have been
developed purely to this end.
The spreadsheet is such a tool and at it's core is array manipulation.

[Simon Peyton Jones](https://en.wikipedia.org/wiki/Simon_Peyton_Jones),
one of the creaters of the
[Haskell programming language](https://en.wikipedia.org/wiki/Haskell),
said of Excel,
> “Most people don’t think of Excel as a programming language at all.
> But it is, right? And moreover, it’s a functional programming language”

The model behind spreadsheets is data is stored in columns
and that formulas can be applied to those columns to generate
new processed columns or aggregate values.

Let's take as an example plotting a function.

<iframe src="https://docs.google.com/spreadsheets/d/1hUX3YHtQL6McZ91IUi1llxhUbd3nmpblgPfhLChj5hw/edit?usp=sharing" width="100%" height="600px" ></iframe>

The spreadsheet above has three columns,
the first of which contains values only, i.e. the numbers 0 to 39.

The second column is a calculated column from the first,
where each entry has a value, `B = (A - 20) / 5`

In the spreadsheet idiom, you type the formula value for the first cell,
`B2`, i.e. `=(A2 - 20) / 5`, and drag it down the column
to indicate that the equivalent calculation is to be performed
for every value in the column.

This can be repeated for further calculated columns, e.g.,
`C = exp(-B * B / 2)`.

This operation of taking a list of values,
and applying a function to each of them is called **map**.
The function *maps* one set of values, e.g. the range [-4, 4],
to another, e.g. the output of a Gaussian function.

The previous example was mathematical in nature, but it need not be,
Another example of mapping using a spreadsheet is mail-merge,
e.g. I have a list of contact details, and I want to produce personalised
invites to an event.

<iframe src="https://docs.google.com/spreadsheets/d/1xp82r4p8V28Y5hMR3FxMcOQKPoJPIjOpEbFAeE9q8uM/" width="100%" height="300px">
</iframe>

In the spreadsheet above, I have details of my friends in two columns,
their name and the group I know them from.
In the example, I want music friends to join on Saturday
and everyone else on Sunday.
Here we have a function that maps an input of `"Music"` to `"Saturday"` and
all other inputs to `"Sunday"`, then a function that combines the names and
day columns to output the invitation.

<iframe src="https://docs.google.com/spreadsheets/d/1CaZOeqaKZMNbPlJIxAt4ONyIexTfSWAXP-7sNVnuGcE/" width="100%" height="400px"></iframe>

## Map

## Filter

## Reduce

## Ramda versions
