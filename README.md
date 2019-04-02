Sets
![Screenshot ](../master/assets/Set_Image_1.png)

WHAT ARE SETS?

"Sets are such a basic notion in mathematics that the only way to ‘define’ them
is by synonyms like collection, class, grouping and so on. A set is completely
characterised by the elements it contains.
There are two main ways of defining a set: (1) by explicitly listing all its
elements or (2) by giving a property that all elements must satisfy."
- from http://www.cs.nott.ac.uk/~pszvc/g51mcs/ch04_sets.pdf

The main difference between sets and array is that you cannot repeat values in a set, and sets are keyed not indexed (so lookup is faster).
Sets are better for keep track of TYPES or ATTRIBUTES of items rather than the number of them. It's better at keeping a log of all the types of fruit in your fruit salad, but not the number of each fruit you used (since values cannot be repeated).

APPLICATIONS OF SETS:
- If we know it advance that we do not want to save duplicate data to our structure
- Want to maintain distinct data with minimal effort 
- You do not care about the order of items in the set

EXAMPLES OF SETS:
- The items you wear: hat, shirt, jacket, pants, and so on
- Types of birds 
- All the different languages

KINDS OF SETS:
- Finite: limited number of members.
- Infinite: unlimited number of members.
- Well-defined: A set is well-defined if there is no ambiguity as to whether or not an object belongs to it, i.e., a set is defined so that we can always tell what is and what is not a member of the set.

https://www.youtube.com/watch?v=rRk0d6P4oUI

```/* Sets */

function mySet() {
    // the var collection will hold the set
    var collection = [];
    // this method will check for the presence of an element and return true or false
    this.has = function(element) {
        return (collection.indexOf(element) !== -1);
    };
    // this method will return all the values in the set
    this.values = function() {
        return collection;
    };
    // this method will add an element to the set
    this.add = function(element) {
        if(!this.has(element)){
            collection.push(element);
            return true;
        }
        return false;
    };
    // this method will remove an element from a set
    this.remove = function(element) {
        if(this.has(element)){
            index = collection.indexOf(element);
            collection.splice(index,1);
            return true;
        }
        return false;
    };
    // this method will return the size of the collection
    this.size = function() {
        return collection.length;
    };
    // this method will return the union of two sets
    this.union = function(otherSet) {
        var unionSet = new mySet();
        var firstSet = this.values();
        var secondSet = otherSet.values();
        firstSet.forEach(function(e){
            unionSet.add(e);
        });
        secondSet.forEach(function(e){
            unionSet.add(e);
        });
        return unionSet;
    };
    // this method will return the intersection of two sets as a new set
    this.intersection = function(otherSet) {
        var intersectionSet = new mySet();
        var firstSet = this.values();
        firstSet.forEach(function(e){
            if(otherSet.has(e)){
                intersectionSet.add(e);
            }
        });
        return intersectionSet;
    };
    // this method will return the difference of two sets as a new set
    this.difference = function(otherSet) {
        var differenceSet = new mySet();
        var firstSet = this.values();
        firstSet.forEach(function(e){
            if(!otherSet.has(e)){
                differenceSet.add(e);
            }
        });
        return differenceSet;
    };
    // this method will test if the set is a subset of a different set
    this.subset = function(otherSet) {
        var firstSet = this.values();
        return firstSet.every(function(value) {
          return otherSet.has(value);
        });
    };
}

var setA = new mySet();  
var setB = new mySet();  
setA.add("a");  
setB.add("b");  
setB.add("c");  
setB.add("a");  
setB.add("d");  
//set a now has a
//set b now has bcad
console.log("the subset of A which is B: " + setA.subset(setB));
console.log("the intersection of A and B: " +setA.intersection(setB).values()); 
console.log("the difference between A and B: " + setB.difference(setA).values());
console.log("the union of A and B: " + setA.union(setB).values());
setA.add("d")
setA.add("m")
//set a is now adm 
 ```
