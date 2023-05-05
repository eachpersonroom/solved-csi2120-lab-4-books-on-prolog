Download Link: https://assignmentchef.com/product/solved-csi2120-lab-4-books-on-prolog
<br>
<h2></h2>

<h3>Exercise 1. Books on Prolog</h3>

Consider a small database that represents books, readers and loans.

% ——–% book( Title, Authors, Publisher, Year, CallNumber )% ——– book(  ‘The craft of Prolog’,  ‘R. A. O”Keefe’,  ‘MIT Press’,  1990,  ‘QA 76.73 .P76 O38 1990’).book(  ‘Programming in Prolog’,  ‘W. F. Clocksin, C. S. Mellish’,  ‘Springer’,  2003,  ‘QA 76.73 .P76 C57 2003’).book(  ‘Prolog for programmers’,  ‘F. Kluzniak, S. Szpakowicz’,  ‘Academic Press’,  1985,  ‘QA 76.73 .P76 K58 1985’).book(  ‘Prolog programming for artificial intelligence’,  ‘I. Bratko’,  ‘Addison-Wesley’,  2001,  ‘Q 336 .B74 2001’). % ——–% reader( CardNumber, Name )% ——– reader( 1234567, ‘James Brown’ ).reader( 2345678, ‘Jacques Brun’ ).reader( 3456789, ‘Giacomo Bruno’ ). % ——–% checkedOut( CardNumber, CallNumber )% ——– checkedOut( 1234567, ‘QA 76.73 .P76 C57 2003’ ).checkedOut( 3456789, ‘Q 336 .B74 2001’ ).

Write the queries that find (1) all books published by Springer, (2) all books published after 1990, (3) all books checked out by James Brown. Next, edit the file to add a few useful entries to each of the three predicates, and run more queries to see that you have not spoiled anything.

<h3>Exercise 2: Relationships</h3>

Given the following database of relationship:

parent(jack,joe).parent(jack,karl).parent(marie,anne).parent(joe,anne).parent(marie,paul).parent(joe,paul).parent(marie,sylvie).parent(bruno,sylvie).parent(anne,zach).parent(tim,zach).parent(sam,tim).parent(emma,tim).parent(josee,sam).parent(gilles,sam).female(marie).female(sylvie).female(anne).female(emma).female(josee).male(karl).male(jack).male(joe).male(bruno).male(paul).male(tim).male(zach).male(sam).male(gilles).

Complete the predicate <em>gmp</em> replacing the <em>?</em> with the appropriate variable. We want to identify the grandmother of Y on the paternal (father’s side) from the facts listed above.

gmp(X,Y) :- parent(?,?),             male(?),             parent(?,?),             female(?).

Test your predicate with the following queries:

1 ?- gmp(emma,zach).true. 2 ?- gmp(marie,paul).false. 3 ?- gmp(X,tim).X = josee ;false. 4 ?- gmp(X,anne).false.

<h3>Exercise 3: Rules and Quiz</h3>

<em>Please hand-in the answer to this question on Virtual Campus during your lab session but at the latest by Friday 6:00pm! Remember, your submission will only count if you have signed the lab attendance sheet.</em> Given the following database:

% Decision to skate home % canal sections% Format is: section number, end point 1, end point 2, distancesection( 1, rideau, mackenzieKing, 0.2 ).section( 2, mackenzieKing, laurier, 0.2 ).section( 3, laurier, somerset, 0.4 ).section( 4, somerset, concord, 0.6 ).section( 5, concord, pretoria, 0.65 ).section( 6, pretoria, fifth, 0.8 ).section( 7, pattersonCreek, pattersonCreek, 0.3 ).section( 8, fifth, lansdowne, 0.7 ).section( 9, lansdowne, bank, 0.45 ).section( 10, bank, bronson, 1.0 ).section( 11, bronson, dowsLake, 0.2 ).section( 12, dowsLakeLoop, dowsLakeLoop, 1.7 ).section( 13, dowsLake, library, 0.6 ). % condition% Format is section number, conditions (green|yellow|red)condition( 1, red ).condition( 2, red ).condition( 3, yellow ).condition( 4, yellow ).condition( 5, yellow ).condition( 6, green ).condition( 7, yellow ).condition( 8, green ).condition( 9, green ).condition( 10, yellow ).condition( 11, yellow ).condition( 12, red ).condition( 13, yellow ).

Fix the predicate isOpen/1 to evalute to true if the conditions on the section with the number X is either green or yellow.

% if conditions on a section are yellow or green, it is open.% This predicate is broken.    isOpen( X ) :- condition( X, yellow ),               condition( X, green ).

Based on the above fix, change the predicate skateHome/0 to be true if all sections between Summerset and Bronson are open. Your solution must use isOpen/0.

% This predicate is broken    skateHome :-    Color = green,    section( X, somerset, concord, _ ),    condition( X, Color ),    section( X, concord, pretoria, _ ),    condition( X, Color ),    section( X, pretoria, fifth, _ ),    condition( X, Color ),    section( X, fifth, lansdowne, _ ),    condition( X, Color ),    section( X, lansdowne, bank, _ ),    condition( X, Color ),    section( X, bank, bronson, _ ),    condition( X, Color )    Color = yellow,    section( X, somerset, concord, _ ),    condition( X, Color ),    section( X, concord, pretoria, _ ),    condition( X, Color ),    section( X, pretoria, fifth, _ ),    condition( X, Color ),    section( X, fifth, lansdowne, _ ),    condition( X, Color ),    section( X, lansdowne, bank, _ ),    condition( X, Color ),    section( X, bank, bronson, _ ),    condition( X, Color ).


