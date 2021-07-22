# Relevant information about 'Diagram of Reactive Systems'

This readme explains the React Agent of the [reactive e-commerce iStar model](https://github.com/UwUnsaac/Ecommerce-Artifacts/blob/main/istar%20models/reactive%20e-commerce%20iStar%20model.png).

## Terms used
- ***(Q)***: Quality
- ***(G)***: Goal
- ***(T)***: Task
- ***(R)***: Resource


## Responsive ***(Q)***
The system responds in a timely manner if at all possible. Responsiveness is the cornerstone of usability and utility, but more than that, responsiveness means that problems may be detected quickly and dealt with effectively. Responsive systems focus on providing rapid and consistent response times, establishing reliable upper bounds so they deliver a consistent quality of service. This consistent behaviour in turn simplifies error handling, builds end user confidence, and encourages further interaction.

* ### Declarative ***(Q)***
  React makes it painless to create interactive UIs. Design simple views for each state in your application, and React will efficiently update and render just the right components when your data changes. [Declarative](https://reactjs.org/) views make your code more predictable and easier to debug.

* ### Components to be rendered ***(G)***
  [ReactDOM](https://reactjs.org/docs/rendering-elements.html) is responsible for rendering the html corresponding to each component in the browser.

* ### That the inputs of the services (functionalities) are rendered ***(G)***
  When interacting with a system, a user and its devices can set the parameters (inputs) needed for rendering the elements to achieve a service

* ### React DOM ***(R)***
  [React DOM](https://reactjs.org/docs/rendering-elements.html) compares the element and its children to the previous one, and only applies the DOM updates necessary to bring the DOM to the desired state. 


## Elasticity ***(Q)***
The system stays responsive under varying workload. Reactive Systems can react to changes in the input rate by increasing or decreasing the resources allocated to service these inputs. This implies designs that have no contention points or central bottlenecks, resulting in the ability to shard or replicate components and distribute inputs among them. Reactive Systems support predictive, as well as Reactive, scaling algorithms by providing relevant live performance measures. They achieve elasticity in a cost-effective way on commodity hardware and software platforms. 

* ### That resources can be automatically managed ***(G)***
  A system must automatically increase or decrease its performance to meet the flow of requests (the demand) as resources are added or removed. 

* ### That the functionality of a component is identified ***(G)***
  When defining the functionality of a component, several strategies can be applied, for the work performed in [uwunssac] we found that a [hierarchicall decomposition] as expressed in a [Feature modeling] can help with the complexity of functionalities. On the other hand, having [delimited consistency] helps in organizing modules according to the resources needed for elasticity

## Message oriented ***(Q)***
Reactive Systems rely on asynchronous message-passing to establish a boundary between components that ensures loose coupling, isolation and location transparency. This boundary also provides the means to delegate failures as messages. Employing explicit message-passing enables load management, elasticity, and flow control by shaping and monitoring the message queues in the system and applying back-pressure when necessary. Location transparent messaging as a means of communication makes it possible for the management of failure to work with the same constructs and semantics across a cluster or within a single host. Non-blocking communication allows recipients to only consume resources while active, leading to less system overhead.

* ### That the states of the components are managed ***(G)***
  The [UseState](https://preactjs.com/guide/v10/hooks/#usestate) accepts an argument, this will be the initial state. When invoked this hook returns an array of two variables. The first being the current state and the second being the setter for our state. Our setter behaves similar to the setter of our classic state. It accepts a value or a function with the currentState as argument.
  When you call the setter and the state is different, it will trigger a rerender starting from the component where that useState has been used.

* ### Delegate tasks asynchronously to other components ***(T)***


## Resilience ***(Q)***
The system stays responsive in the face of failure. This applies not only to highly-available, mission-critical systems — any system that is not resilient will be unresponsive after a failure. Resilience is achieved by replication, containment, isolation and delegation. Failures are contained within each component, isolating components from each other and thereby ensuring that parts of the system can fail and recover without compromising the system as a whole. Recovery of each component is delegated to another (external) component and high-availability is ensured by replication where necessary. The client of a component is not burdened with handling its failures.

* ### Delegation ***(Q)***
  Delegating a task asynchronously to another component means that the execution of the task will take place in the context of that other component. This delegated context could entail running in a different error handling context, on a different thread, in a different process, or on a different network node, to name a few possibilities. The purpose of delegation is to hand over the processing responsibility of a task to another component so that the delegating component can perform other processing or optionally observe the progress of the delegated task in case additional action is required such as handling failure or reporting progress.

* ### Isolation and Containment ***(Q)***
  Isolation can be defined in terms of decoupling, both in time and space. Decoupling in time means that the sender and receiver can have independent life-cycles—they do not need to be present at the same time for communication to be possible. It is enabled by adding asynchronous boundaries between the components, communicating through message-passing. Decoupling in space (defined as Location Transparency) means that the sender and receiver do not have to run in the same process, but wherever the operations division or the runtime itself decides is most efficient—which might change during an application's lifetime.

  True isolation goes beyond the notion of encapsulation found in most object-oriented languages and gives us compartmentalization and containment of:
  - State and behavior: it enables share-nothing designs and minimizes contention and coherence cost (as defined in the Universal Scalability Law);
  - Failures: it allows failures to be captured, signalled and managed at a fine-grained level instead of letting them cascade to other components.

  Strong isolation between components is built on communication over well-defined protocols and enables loose coupling, leading to systems that are easier to understand, extend, test and evolve.

* ### That the functioning is asynchronous ***(G)***

* ### Run sender and receiver in different processes ***(T)***
  [Async-Await](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Async_await) basically act as syntactic sugar on top of promises, making asynchronous code easier to write and to read afterwards. They make async code look more like old-school synchronous code, so they're well worth learning.

* ### Replication ***(Q)***
  Executing a component simultaneously in different places is referred to as replication. This can mean executing on different threads or thread pools, processes, network nodes, or computing centers. Replication offers scalability, where the incoming workload is distributed across multiple instances of a component, or resilience, where the incoming workload is replicated to multiple instances which process the same requests in parallel. These approaches can be mixed, for example by ensuring that all transactions pertaining to a certain user of the component will be executed by two instances while the total number of instances varies with the incoming load

* ### That component reuse is allowed ***(G)***

* ### Create an ideal component architecture ***(T)***
  Towards the achievement of replication, the reuse of components can be satisficed if  our code architecture respects the principles of [low coupling and high cohesion](https://enterprisecraftsmanship.com/posts/cohesion-coupling-difference/)

* ### Reduce coupling ***(T)***
* ### Increase cohesion ***(T)***

## The sources used in this description are taken from the following websites:

1. Declarative React. Available in: https://reactjs.org/
2. React DOM. Available in: https://reactjs.org/docs/rendering-elements.html
3. React, UseState. Available in: https://preactjs.com/guide/v10/hooks/#usestate
4. Async-Await. Available in: https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous/Async_await
5. Cohesion and Coupling. Available in: https://enterprisecraftsmanship.com/posts/cohesion-coupling-difference/
