# Advanced styling

## The show rule
```
Advanced styling comes with another rule. The _`show` rule_.

#show "Be careful": strong[Play]

This is a very powerful thing, sometimes even too powerful.
Be careful with it.

#show "it is holding me hostage": text(green)[I'm fine]

Wait, what? I told you "Be careful!", not "Play!".

Help, it is holding me hostage.
```

## Now a bit more serious

```
Show rule is a powerful thing that takes a _selector_
and what to apply to it. After that it will apply to
all elements it can find.

It may be extremely useful like that:

#show emph: set text(blue)

Now if I want to _emphasize_ something,
it will be both _emphasized_ and _blue_.
Isn't that cool?
```

## Selector

```
So show rule can accept selectors.
There are lots of different selector types,
for example
- element functions
- strings
- regular expressions
- field filters

Let's see example of the latter:

#show heading.where(level: 1): set align(center)

= Title
== Small title

Of course, you can set align by hand,
no need to use show rules
(but they are very handy!):

#align(center)[== Centered small title]
```

## Custom formatting

```
Let's try now writing custom functions. 
It is very easy, see yourself:

#show heading: it => {
  // center it
  set align(center)
  // set size and weight
  set text(12pt, weight: "regular")
  // see more about blocks and boxes
  // in corresponding chapter
  block(smallcaps(it.body))
}

= Smallcaps heading
```

## Formatting to get an article look

```
#set page(
  // Header is that small thing on top
  header: align(
    right + horizon,
    [Some header there]
  ),
  height: 12cm
)

#align(center, text(17pt)[
  *Important title*
])

#grid(
  columns: (1fr, 1fr),
  align(center)[
    Some author \
    Some Institute \
    #link("mailto:some@mail.edu")
  ],
  align(center)[
    Another author\
    Another Institute \
    #link("mailto:another@mail.edu")
  ]
)

Now let's split text into two columns:

#show: rest => columns(2, rest)

#show heading.where(
  level: 1
): it => block(width: 100%)[
  #set align(center)
  #set text(12pt, weight: "regular")
  #smallcaps(it.body)
]

#show heading.where(
  level: 2
): it => text(
  size: 11pt,
  weight: "regular",
  style: "italic",
  it.body + [.],
)

// Now let's fill it with words:

= Heading 
== Small heading
#lorem(10)
== Second subchapter
#lorem(10)
= Second heading
#lorem(40)

== Second subchapter
#lorem(40)
```