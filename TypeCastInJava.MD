#### Checked Casts at Run Time 

Here is the algorithm to check whether the run-time type R of an object is assignment compatible with the type T which is the erasure (§4.6) of the type named in the cast operator. If a run-time exception is thrown, it is a ClassCastException.

1. If R is an ordinary class (not an array class):

    - If T is a class type, then R must be either the same class (§4.3.4) as T or a subclass of T, or a run-time exception is thrown.

    - If T is an interface type, then R must implement (§8.1.5) interface T, or a run-time exception is thrown.

    - If T is an array type, then a run-time exception is thrown.

2. If R is an interface:

    - If T is a class type, then T must be Object (§4.3.2), or a run-time exception is thrown.

    - If T is an interface type, then R must be either the same interface as T or a subinterface of T, or a run-time exception is thrown.

    - If T is an array type, then a run-time exception is thrown.

