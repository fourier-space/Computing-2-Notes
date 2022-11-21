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

<iframe src="https://docs.google.com/spreadsheets/d/1xp82r4p8V28Y5hMR3FxMcOQKPoJPIjOpEbFAeE9q8uM/" width="100%" height="400px">
</iframe>

In the spreadsheet above, I have details of my friends in two columns,
their name and the group I know them from.
In the example, I want music friends to join on Saturday
and everyone else on Sunday.
Here we have a function that maps an input of `"Music"` to `"Saturday"` and
all other inputs to `"Sunday"`, then a function that combines the names and
day columns to output the invitation.

The second common spreadsheet operation is filtering.
We decide to show some data rows and hide others.

<iframe src="https://docs.google.com/spreadsheets/d/1CaZOeqaKZMNbPlJIxAt4ONyIexTfSWAXP-7sNVnuGcE/" width="100%" height="500px"></iframe>

In this example, we have a dataset of students and which elective module they
are enrolled on.
For our purposes, we only want to view students who are enrolled on
Design Psychology.
To do this, we make use of a *predicate function*
– a function that returns `true` or `false` –
and we can filter to show only rows where the filter returns `true`.
In this case the predicate is `= B="Design Psychology"`.
In the example, there are two sheets,
"Filter" and "Filter – Only Design Psychology"
which shows the the dataset before and after the filter.

The last example we'll look at in spreadsheet terms is when we want to
aggregate a dataset to a single value.
This operation is called *reduce* because we are taking a list of values
and reducing it to a single value.

The simplest example of this is taking a sum of a list of numbers,
our input is a whole list, and our output is a single number that is the sum.
There are a lot of these reducing functions built into spreadsheet software,
such as `SUM`, `AVERAGE`, `CONCATENATE`, `STDEV`, etc.

<iframe src="https://docs.google.com/spreadsheets/d/1OLmw-YPvd0VbtKnbUfZ2UCdOsAh5ceMUSf8LEW0vdIo" width="100%" height="500px"></iframe>

We show some aggregating functions in the spreadsheet above.

Some of these functions can be constructed by repeatedly
applying an operation over two inputs.
For example, with `SUM` which works on a list,
we have the plus operator, `+`, which works on a pair of numbers.
The output of `SUM` is come to by successively adding together each element.
`SUM(1, 2, 3, 4) = ((1 + 2) + 3) + 4`.
We've put the brackets here to emphasise the order that the addition is
being done.
We're creating a running total as we go,

<iframe src="https://docs.google.com/spreadsheets/d/1fzUuZC-iDX7-6K5-RZ_toCmLGD5IG30AT_pTdprqUJg" width="100%" height="500px"></iframe>

## Map

## Filter

## Reduce

## Ramda versions
