Different patterns that software follows with it's design. Think about how it changes data/starts events.

## Adapter
Making so that one system can work with a different system.
- You become the middle man
- You're transforming data to match each platform's specifications
## Facade
A simplified interface to a system
- You are a middle man
- Reduced bugs and unnecessary coding
- A reduced feature set compared to the primary system
	- Hide what doesn't matter

> EX: Block code
## Strategy
A factory pattern, when you want to create objects.
## Publish and Subscribe
Interact with events and notify the interested parties
- You could create the events, or you could just read them
- Not everyone is interested in every message
	- Make sure people can filter their notifications
> Used often in social media