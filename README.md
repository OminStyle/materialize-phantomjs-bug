# Meteor Materialize Spiderable Bug

Bug report for [materialize](https://github.com/Dogfalo/materialize). Adding [materialize:materialize](https://atmospherejs.com/materialize/materialize) to a [Meteor](https://www.meteor.com/) project breaks spiderable. Deploying to meteor.com and [modulus](https://modulus.io/) give same results. Links for deployed projects with and without materialize package are provided in Results.

## Packages Used
* ongoworks:spiderable (https://atmospherejs.com/ongoworks/spiderable)
* dfischer:phantomjs (https://atmospherejs.com/dfischer/phantomjs)
* materialize:materialize (https://atmospherejs.com/materialize/materialize)

## Steps to Reproduce
1. Create a meteor project
2. ```cd PROJECT-NAME/```
3. ```meteor add ongoworks:spiderable dfischer:phantomjs```
5.``` meteor deploy PROJECT-NAME.meteor.com```
6. ```curl PROJECT-NAME.meteor.com/?_escaped_fragment_=```
7. Confirm that <body> is not empty
8. ```meteor add materialize:materialize```
9. ```meteor deploy PROJECT-NAME.meteor.com```
10. ```curl PROJECT-NAME.meteor.com/?_escaped_fragment_=```
11. <body> is now empty

## Results
I get the following error message on Modulus: 

```spiderable: phantomjs failed: { [Error: Command failed: ] killed: true, code: 1, signal: null }```

You can use ```curl``` and add ```/?_escaped_fragment_=``` to the end of the url to mimic Googlebot.
* With materialize:materialize package http://spiderable-with-materialize.meteor.com
* Without materialize:materialize package http://spiderable-without-materialize.meteor.com

