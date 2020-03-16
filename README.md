# Simple Behavior Tree Editor
Explanation of components
<br>
Decorator is the base class for all decorator nodes. Thus, if you want to create new custom decorator nodes, you need to inherit from this class.

Conditioin is the base class for all condition nodes. Thus, if you want to create new custom condition nodes, you need to inherit from this class.

Sequence ticks its children sequentially until one of them returns `FAILURE`, `RUNNING` or `ERROR`. If all children return the success state, the sequence also returns `SUCCESS`.

Selector ticks its children sequentially until one of them returns `SUCCESS`, `RUNNING` or `ERROR`. If all children return the failure state, the priority also returns `FAILURE`.

MemSequence is similar to Sequence node, but when a child returns a `RUNNING` state, its index is recorded and in the next tick the MemSequence call the child recorded directly, without calling previous children again.

MemSelector is similar to Priority node, but when a child returns a `RUNNING` state, its index is recorded and in the next tick the, MemPriority calls the child recorded directly, without calling previous children again.

The Inverter decorator inverts the result of the child, returning `SUCCESS` for `FAILURE` and `FAILURE` for `SUCCESS`.

The Limiter decorator limits the number of times its child can be called. After a certain number of times, the Limiter decorator returns `FAILURE` without executing the child.

Repeater is a decorator that repeats the tick signal until the child node return `RUNNING` or `ERROR`. Optionally, a maximum number of repetitions can be defined.

The Limiter decorator limit the number of times its child can be called. After a certain number of times, the Limiter decorator returns `FAILURE` without executing the child.

RepeatUntilFailure is a decorator that repeats the tick signal until the node child returns `FAILURE`, `RUNNING` or `ERROR`. Optionally, a maximum number of repetitions can be defined.

RepeatUntilSuccess is a decorator that repeats the tick signal until the node child returns `SUCCESS`, `RUNNING` or `ERROR`. Optionally, a maximum number of repetitions can be defined.

Failure, Runner, Succeeder, Wait, Error are all leaf nodes

*** Note that *** new nodes like composite, decorator, action and condition can be made as needed.
