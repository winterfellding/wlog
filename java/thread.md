### start

	一个Thread只能启动一次，具体可见于start方法
	public synchronized void start() {
        /**
         * This method is not invoked for the main method thread or "system"
         * group threads created/set up by the VM. Any new functionality added
         * to this method in the future may have to also be added to the VM.
         *
         * A zero status value corresponds to state "NEW".
         */
        if (threadStatus != 0)
            throw new IllegalThreadStateException();

        /* Notify the group that this thread is about to be started
         * so that it can be added to the group's list of threads
         * and the group's unstarted count can be decremented. */
        group.add(this);

        boolean started = false;
        try {
            start0();
            started = true;
        } finally {
            try {
                if (!started) {
                    group.threadStartFailed(this);
                }
            } catch (Throwable ignore) {
                /* do nothing. If start0 threw a Throwable then
                  it will be passed up the call stack */
            }
        }
    }
	
	一旦启动，threadStatus就不是NEW状态了，也即是不为0，第二次调用start方法就会抛出Exception
	
### Main thread

	public class MyThread extends Thread {
	
		public int x = 0;
	
		@Override
		public void run() {
			for (int i = 0; i < 100; i++) {
	            try {
	                Thread.sleep(10);
                } catch (InterruptedException e) {
	                e.printStackTrace();
                }
			System.out.println(x++);
		}
	}
	
	/**
	 * main 线程会先跑，之后才跑MyThread对应线程，
	 * 但如果加入join方法，就会先跑MyThread的线程
	 */
	public class Test {
		public static void main(String[] args) throws InterruptedException {
	    	MyThread mt = new MyThread();
	    	mt.start();
	    	// mt.join();
	    	System.out.println(100);
    	}
	}
	
### Executor

	可以通过java.util.concurrent.ExecutorService来调用一个多线程任务
	ExecutorService exec = Executors.newCachedThreadPool();
	exec.execute(runnableReference);
	
### Runnable与Callable

	除了Runnable接口，还有一个借口叫做Callable，Runnable继承之后不可以把值return出来，Callable接口
	可以做到，一个类实现Callable接口，然后使用ExecutorService的submit方法调用，会得到一个Future<T>对象，
	使用该对象的get方法，即可获得在Callable接口中定义的return值。