# JS Day 1 Homework

Go through each sample code and work out what the output will be and explain what happened.

### Episode 1
```js
var name = 'Keith';

var printName = function() {
  console.log('My name is ' + name );
};

printName();

```
#### Answer
Variable 'name' is declared outside the following printName function therefore it has scope (is visible) within that function. printName is defined as an anonymous function, which when called will output the given sentence using the name variable.

### Episode 2
```js
score = 5;

var result = function() {
  var score = 3;
  return score;
};

console.log(result());

```
#### Answer
Because the variable 'score' is declared outside the 'result', score has global scope, regardless of whether or not 'var' is used, so it can be accessed from within 'result'.  Because var score is assigned inside the function -after- the initial assignment, the latter value will be true.  'score' will be output as 3.

### Episode 3
```js
var myAnimals = ['Chickens', 'Cats', 'Rabbits'];

var listAnimals = function() {
  myAnimals = ['Ducks', 'Dogs', 'Lions'];
  for(var i=0;i<myAnimals.length; i++){
    console.log(i + ": " + myAnimals[i]);
  }
}

listAnimals();

```
#### Answer
Again, because myAnimals variable is declared twice, the console will output the latterly assigned values.  The loop will output the index of the loop/array, followed by the value at that point - i.e. 0: Ducks, 1: Dogs...etc.

### Episode 4

```js
var suspectOne = 'Jay';
var suspectTwo = 'Val';
var suspectThree = 'Keith';
var suspectFour = 'Rick';

var allSuspects = function() {
  var suspectThree = 'Harvey'
  console.log('Suspects include: ' + suspectOne + ', ' + suspectTwo + ', ' + suspectThree + ', ' + suspectFour)
};

allSuspects();
console.log( 'Suspect three is:' + suspectThree );
```
#### Answer
The allSuspects function outputs a list of all the suspects when called.  Suspect three will be declared as Harvey from the allSuspects() function, because it is the latter declared value and overwrites the initial variable which has Keith as a value.  When console.log() is used outside the allSuspects function, suspectThree = Harvey only exists as a local variable inside that function and therefore can't be accessed for the log output - which is why Keith is returned on this occasion.

### Episode 5

```js
var detective = {
  name : 'Ace Ventura',
  pet : 'monkey'
};

var printName = function(detective) {
  return detective.name
};

var detectiveInfo = function() {
  detective['name'] = 'Poirot'
  return printName(detective);
};

console.log(detectiveInfo());
```
#### Answer
'Poirot' should be returned from this console.log(), as the initially assigned detective name is being overwritten inside the detectiveInfo function.

### Episode 6
```js
var murderer = 'rick';

var outerFunction = function() {
  var murderer = 'marc';

  var innerFunction = function() {
    murderer = 'valerie';
  }

  innerFunction();
}

outerFunction();
console.log('the murderer is ', murderer);
```
#### Answer
What appears to be happening is that within the outerFunction, the assignment of marc overrides the assignment of valerie, as it's a layer outside the function valerie is declared. Since, marc is assigned only as a local variable however, it can't be read by the console log output, so rick is the final output value.  If you comment out marc, valerie is output since that is the last assigned value.

I'd have said initially however, that the output value here should be 'valerie' since it's a global variable, and the last assignment made, with innerFunction, so I'm not entirely sure I understand why this is happening.

### Episode 7 - Make up your own episode/s!

Make up your own episode which can be whatever you wish and the rest of the class will work out together what happened and what the output will be.

#### Answer
```js
var fruit = 'orange';

var fruitGenerator = function(){
   let fruit = 'apple';
   fruitTwister = function(){
      fruit = 'grapefruit';
      fruitHeadSpinner = function(){
         const fruit = 'grape';
      }
      fruitHeadSpinner();
   }
   fruitTwister();
}

fruitGenerator();
fruitTwister();
fruitHeadSpinner();
console.log(fruit)

```
