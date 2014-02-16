##### Define an abstract claass / interface as Command

	public abstract class Command {

		public abstract void execute();

		public abstract void unDo();

	}

When you have an command, extends abstract class / implements interface, 
	
	public classs ShoppingCommand extends Command {
		public void execute() {
			System.out.println("Shopping in xxx");
		}
	
		public void unDo() {
			System.out.println("I'm home~");
		}
	}
When you need to create an Command, you can use `Command c = new ShoppingCommand();`, and use data inject or construtor inject to set it into 
another object, e.g.

	public class Person {

		private List<Command> commands = new ArrayList<>();

		public void addCommand(Command c) {
			this.commands.add(c);
		}

		public void executeCommands() {
			for (Command c : commands) {
				c.execute();
			}
		}
	}
You can new some commands and use the addCommand to inject it into the commands list, and use the executeCommands to execute at once. 