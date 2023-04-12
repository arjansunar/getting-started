## 💁 Intro

Rxjs provides methods and classes that allow users to implement the `Push` based flow of
Data architecture.

> Think of RxJS as Lodash for events.

The essential concepts in RxJS which solve async event management are:

- [Observable](#🚰-observables): represents the idea of an invokable collection of future values or events.
- [Observer](#🔭-observer): is a collection of callbacks that knows how to listen to values delivered by
  the Observable.
- [Subscription](#subscriptions): represents the execution of an Observable, is primarily useful for
  cancelling the execution.
- [Operators](): are pure functions that enable a functional programming style of dealing
  with collections with operations like `map`, `filter`, `concat`, `reduce`, etc.
- [Subject](): is equivalent to an EventEmitter, and the only way of multicasting a value or
  event to multiple Observers.
- [Schedulers](): are centralized dispatchers to control concurrency, allowing us to
  coordinate when computation happens on e.g. setTimeout or requestAnimationFrame or others.

### 🚰 Observables:

Its a stream of data that can be subscribed to. It can be thought of as a sequence of array that unfolds as time moves on.

### 🔭 Observer:

Observer is the entity that can access the stream of data provided by an `Observable`. It listens to the events/data that flows through. It can implement the following methods:

> Observers are consumer of values delivered by an Observable.

- next() => returns the next value in the stream
- error() => returns the error value incase error occues in the setream
- complete() => signals the completion of an Observable event

> Check out [marble diagram](https://rxjs.dev/guide/operators) for visualizing Rxjs concepts

### Subscriptions:

Its an object which represents a disposable resource (execution of Observable). Subscription have the `unsubscribe` method that disposes the resource held by an `Observable`.
