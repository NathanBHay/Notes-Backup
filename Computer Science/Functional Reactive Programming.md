Functional Reactive Programming is an approach to [[Functional Programming|function prgramming]] that is used to model complex asynchronous behaviours. These operations are done through observable data structures which wrap collections of things in containers similar to objects. This creates a stream which can be initialised through a **subscription** operation. This passes an effectful function which applies to the stream. A stream can be used to handle UI or communication events as there stream isn't generated until an event occurs. Observable streams commonly have variable names which end with a `$`.

# Observable Creation
Observable data structures can be created with the following functions:
- **Of** which creates an observable that emits the specified elements in its parameter list in order. This happens similar to a lazy sequence except nothing happens until the stream is initialised.
- **Range** creates a stream of numbers from one number to another.
- **From Event** produces a stream for the specified event. This stream should be specified by a type parameter.
- **Interval** produces a stream of increasing numbers emitted every millisecond.

# Observable Combination
Observable streams can be combined through these operations:
- **Zip** function provides a way to pair the values of two streams into an array. This merges the streams.
- **Merge** operation functions similar to a concatenate operation but on streams.

# Observable Methods
Some methods which change the observable object itself are:
- **Pipe** is an operation which chains functional operations such as **map** or **filter**.
- **Subscribe** does an operation which effects the state of the program.

# Operators
These are operations which can be done within observable streams. These are:
- **Map** transforms the elements of a stream.
- **Filter** takes out elements of the stream.
- **Take** takes a certain number of elements.
- **Last** takes the last element.
- **Scan** is an operation similar to reduce however it applies to an accumulator function coming through an observable, instead of a single value such as reduce. It therefore emits a stream of running accumulation.
- **Merge Map** operation gives the cartesian product of two streams. This works through an operation which defines `column=>row` as to create the product.
