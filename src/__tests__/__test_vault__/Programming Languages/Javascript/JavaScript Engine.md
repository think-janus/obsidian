- How a JS Engine works:
	- Steps to run code:
		- Loading Phase:
			- [[Tokenization]]
			- [[Parsing]] to AST
			- Convert to [[Bytecode]]
				- [[Spidermonkey]] will lazily convert functions to byte code, doing it [[Just in Time]] in a process called delazification
		- Evaluation Phase
			- The interpretter runs the bytecode
			- Blocks of byte codes that get called frequently may get promoted by the [[Just In Time Compiler]] to be compiled to machine code for faster execution (instead of the byte code being run)
	- Call stack is effectively maintained by keep track of the stack of function execution contexts (which has all the information needed to bind variables etc)
	- Event Loop:
		- There is a single thread in most engines. The thread is in charge of executing everything on the call stack until there are no more execution contexts
		- There are two queues for completed asynchronous code to wait on: The Callback / Task queue for long operations like network requests, and the Microtask queue for small operations like Promises
		- Once the stack is empty, callbacks for microtasks are run, and if that is empty then the callback queue
	[[ES Module System]]