# Subjects

Refresher on the Observer Pattern:

Observers are classes with a notification method on them. They are literally 'observing' a subject. Imagine students to a teacher. The teacher, or subject, has the ability to add and remove students, or observers, and notify them when state changes. When the subject sends the notification, all observers receive the same data. This is referred to as 'multicast'.

This connecting of observers to an observable is what subjects are all about. They’re able to do it because subjects themselves are both observers and observables.

Subjects are useful when you need to multicast (they multicast to an internal list of observers), unlike Observables which default to unicast.

Unicast: each subscribe observer owns an independent execution of the Observable

Subjects are like EventEmitters in that they maintain a registry of many listeners

ex:
```javascript
import * as Rx from "rxjs";

const observable = Rx.Observable.create((observer) => {
    observer.next(Math.random());
});

// subscription 1
observable.subscribe((data) => {
  console.log(data); // 0.24957144215097515 (random number)
});

// subscription 2
observable.subscribe((data) => {
   console.log(data); // 0.004617340049055896 (random number)
});
```

Multicast: one observable execution is shared by all subscribers
```javascript
import * as Rx from "rxjs";

const subject = new Rx.Subject();

// subscriber 1
subject.subscribe((data) => {
    console.log(data); // 0.24957144215097515 (random number)
});

// subscriber 2
subject.subscribe((data) => {
    console.log(data); // 0.24957144215097515 (random number)
});

subject.next(Math.random());
```

Probably a more important distinction between Subject and Observable is that a Subject has state, it keeps a list of observers. On the other hand, an Observable is really just a function that sets up observation. Whereas Observables are soley data producers, Subjects can be used as a producer and consumer. Use Subjects if your Observables subscriptions receive different values.

## References
- https://medium.com/@benlesh/on-the-subject-of-subjects-in-rxjs-2b08b7198b93
- https://medium.com/@luukgruijs/understanding-rxjs-subjects-339428a1815b
- https://blog.angularindepth.com/rxjs-understanding-subjects-5c585188c3e1
- https://github.com/ReactiveX/rxjs/blob/master/doc