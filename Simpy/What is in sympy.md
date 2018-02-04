#What is in sympy
---
*  Process: Active object of interest. Like ants, cars components.

*  Environment: Then environment that processes runs in.

*  Event: The activity conducted by processes

*  The process yields an event and goes to sleep. When the event is triggered, the process is woken and resumes running.

*  The time in simpy environment is virtual time. Processes update the environment time honestly and to achieve virtual concurrency, and consistency in time.

  ## Remark: Most useful guides are covered in topical guides.

  ​

  ---

  # The creation of a process

  ---

  * Call env.process(function()), a process under the name of env is created, ready to execute the function() procedure

  # Running the processes in an environment

  ---

  * Call env.run(until=condition is met/event is triggered), all processes in the environment starts to run until condition is met or event is triggered, then the env stops simulation.

  ##Remark: it is extremely easy to forget that you have created some process inside the initialization of some object or at some hard-to-notice places, explicitly highlight the creation of processes are important!

  ---

  #	Waiting for  an event

  ```python
  yeild env.process(another_procedure())	#Create another process under env, who is ready to execute another_procedure(). Then call yield and give out the cpu time to others. Wakeup when the new process yields.
  ```

  ---

  # Time out

  * Simpy has time scale system built in the env object, we can update the env time by calling yielding env.timeout(delay=xx)

  # Interruption

  ---

  ```python
  proc1=env.process(function())
  #call interrupt() to fire and interrupt on proc1
  proc1.interrupt()
  ```

  ```python
  #inside proc1, it is expected there is some exception handling code
  try:
      ...
  except simpy.Interrupt:
      ...
  ```

  * Interrupts are used to signal between processes.

  # Wait on resources(request(), release(0))

  ---

  ```python
  resource=simpy.Resource(env,capacity=5) #Creation of resource to be used in env, with capacity 5.

  ...

  yield resource.request() # Die out and send request. Like lock_acquire(). Or P(xx) in semaphore.

  somecode()

  resource.release() # Like V(xx) in semaphore.
  ```

  * Exactly like a semaphore.

  # 3 ways to trigger an event

  ---

  ```python
  #yielding, waiting for an event to be triggered
  env=simpy.Environment()
  event=env.event() #Here we create a new event object, untriggered, under env.

  ...some code

  yield event # Normally this is yielding to the reference of the event, the event can be shared among mutiple processes. The yield is not going to wake up  until event is triggered.

  ...another page
  event.trigger()/event.succeed()/event.fail() # 3 ways to trigger the events globally, wakes up every one sleeping on this event. And the event expired in the env, normally needs to be reset.
  ```

  ## Remark: Processes are events too, that is why we can yield env.process()

  # Waiting on one or multiple or all events

  ```python
  >>> from simpy.events import AnyOf, AllOf, Event
  >>> events = [Event(env) for i in range(3)]
  >>> a = AnyOf(env, events)  # Triggers if at least one of "events" is triggered.
  >>> b = AllOf(env, events)  # Triggers if all each of "events" is triggered.
  ```

  ```python
   #Logical operators on multiple events.
      t1, t2 = env.timeout(1, value='spam'), env.timeout(2, value='eggs')
  ...     ret = yield t1 | t2
  ...     assert ret == {t1: 'spam'}
  ...
  ...     t1, t2 = env.timeout(1, value='spam'), env.timeout(2, value='eggs')
  ...     ret = yield t1 & t2
  ...     assert ret == {t1: 'spam', t2: 'eggs'}
  ...
  ...     # You can also concatenate & and |
  ...     e1, e2, e3 = [env.timeout(i) for i in range(3)]
  ...     yield (e1 | e2) & e3
  ...     assert all(e.processed for e in [e1, e2, e3])
  ...
  ```

  ​
