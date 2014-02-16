##### Factory

	First, make the constructor private, to make the other class can not new the object.
	Second, provide a static method, getInstance() to get the Object refrence.

	public class Car {
		
		public static Car getInstance() {
			return new Car();
		}
		
		public void run() {
			System.out.println("Running~");
		}
		
		private Car() {}
	}


	public class CarMain {
		public static void main(String[] args) {
			Car c = Car.getInstance();
			c.run();
		}
	}

If we want it always get the same refrence, we can change `Car` class to:

	public class Car {
		
		private static Car car = new Car();
		
		public static Car getInstance() {
			return car;
		}
		
		public void run() {
			System.out.println("Running~");
		}
		
		private Car() {}
	}

You always get the same Car, and this is `Singleton`, and the static method `getInstance` use the `static factory` pattern.

When we want to abstract Car, we can define an interface `Moveable`

	pubilc interface Moveable {
		// interface the method default to public
		void run();
	}

	public class Car implements Moveable {
		public void run() {
			System.out.println("Running~");
		}
	}

	public abstract class VehicleFactory {
		public Moveable create();
	}

	public Class CarFactory extends VehicleFactory {
		public Moveable create() {
			return new Car();
		}
	}
With this abstraction, we can make it easy to add new things, e.g. we want to add a new PlaneFactory, we can just  extends the VehicleFactory

	public class PlaneFactory extends VehicleFactory {
		public Moveable create() {
			return new Plane();
		}
	}

When we use these class in the Main Service class, we can just change the new subFactory, and the other code needn't to be changed.