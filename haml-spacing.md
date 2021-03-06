Haml Spacing
============

To help keep some level of sanity, use the Layout/Root/Interior (`LRI`) method of spacing in `Haml` files:

Layout
------

**Layout** elements are grouped together and followed by a single-line space.

```haml
/ Layout
.row
  .cell.well
  
    / ...
    
/ Layout
.row
  .cell.well
    .g
      .g-b.g-b--1of2
  
        / ...
        
      .g-b.g-b--1of2
  
        / ...
```

Root
----

**Root** elements inside of **Layout** elements receive a single-line space after each element.

```haml
/ Layout
.row
  .cell.well
  
    / Root
    %ul.list
      %li.list-item Item
      %li.list-item Item
      %li.list-item Item
      %li.list-item Item
      
    / Root
    %ul.list
      %li.list-item Item
      %li.list-item Item
      %li.list-item Item
      %li.list-item Item
```

Interior
--------

**Interior** elements inside of **Root** elements receive a single-line space in between.

```haml
/ Layout
.row
  .cell.well
    .g
      .g-b.g-b--1of2
      
        / Root
        .card.card--a
          
          / Interior
          %ul.list
            %li.list-item Item
            %li.list-item Item
            %li.list-item Item
            %li.list-item Item
          
      / Layout
      .g-b.g-b--1of2
      
        / Root
        .card.card--a
        
          / Interior
          %ul.list
            %li.list-item Item
            %li.list-item Item
            %li.list-item Item
            %li.list-item Item
            
          / Interior
          %p This is another element.
          
          / Interior
          %a{ href: '#' } And a link!
```

**Note**: If there is a _single_ **Interior** element inside of a **Root** element, you can opt to omit the space, only adding it once there are more **Interior** elements. For example:

```haml
/ Layout
.row
  .cell.well
    .g
      .g-b.g-b--1of2
      
        / Root
        .card.card--a
          / Interior
          %ul.list
            %li.list-item Item
            %li.list-item Item
            %li.list-item Item
            %li.list-item Item
```

Ruby Conditionals & Loops
-------------------------

Follow the **LRI** rules above for conditionals and loops as well. For example:

### Conditionals

```haml
- if conditional
  %p The conditional is true, so show this thing.
- else
  %p The conditional is false, so show this thing.
```

_There is only a single element, so no newline is created._

```haml
- if conditional

  %p The conditional is true, so show this thing.
  
  = link_to 'Button', '/', class: 'btn'
  
- else

  %p The conditional is false, so show this thing.
  
  = link_to 'Button', '/', class: 'btn'
```

_There are multiple elements, so a newline is created._

### Loops

```haml
- things.each do |thing|
  %p= thing.title
```

_There is only a single element, so no newline is created._

```haml
- things.each do |thing|

  .card
    
    %p= thing.title
    
    = link_to 'Button', '/', class: 'btn'
```

_There are multiple elements, so a newline is created._
