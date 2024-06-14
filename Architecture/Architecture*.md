* Global state makes program state unpredictable (why?)
* Actually, it favors side effects
* You can't test properly a program if the side effects affects variables out of scope
* Most of legacy software uses things like e2e tests because it abuses the global state
* Side effects thus affects how you can't think about the flow of the code. You can effectively predict the flow of the code if it don't have any side effects. The contrary is true
* It's impossible to not have global state at all. Better use Dependency Injection to be explicit about Global State, using Singleton's or a explicit state value
* The code of a module or an unikt shouldn't care where state comes from (it includes static variables, thread local, etc). Good to wrap the Thread Local and static vars inside an object and provide it via DI
* It includes every direct call to `useContext`, I think. You make custom hooks to hide the `useContext` to effectively mock the calls 
* Namely, Global State are generally public and readed by any part of the program. It means that the entire program can, potentially, be coupled by the global state, difficulting any refactoring
* Never think about this, but, how prop drilling can be an indicative of design flawness?
* Cronjobs can be mean of `globals`, but with timers. The cronjobs and background jobs runs every time, regardless of some state or some trigger
* Global state goes for inflexibility, as goes for requiring mutating the global state
* If we have a global state, it means this state is one and only. If I need to mutate, I need a lock to guarantee that other threads cannot mutate it at the same time
* I think, the best thing to avoid global state is to make the relevant data for a single context imutable. It can be made by passing as parameter and with immutable dependency injection
* Dependency Injection frameworks simplifies the resolution of Dependency Graphs, because, the dependency management will be automatized and the refactoring would be more easy. The system would be easier to change

## 12 factor app
3. Store config that may varies between deploys in ENV VARS
   1. For Golang, you can use a makefile that gonna call your app, passing the env vars to cli args 
4. 