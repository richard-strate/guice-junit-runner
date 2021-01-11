guice-junit-runner
====

This is a forked version of [guice-junit-runner](https://github.com/marcolamberto/guice-junit-runner) 1.0.2. It was created as I didn't get the original to build. It is not built or release on any public site.

# From marcolamberto

A Guice JUnit Runner

## What is guice-junit-runner?

guice-junit-runner is a JUnit Runner allowing Guice-based testing.
Each test method is running with a clean Injector instance.

## Basic usage

```java
@RunWith(GuiceJUnitRunner.class)
public class GuiceJUnitRunnerTest {
	@Inject
	public MyService service;

	@Test
	public void test() {
		// ...
	}
}
```

## Using custom Guice modules

You can easily add one more modules by using the @GuiceModules annotation.

```java
@RunWith(GuiceJUnitRunner.class)
@GuiceModules(TestModule.class)
public class GuiceJUnitRunnerTest {

	public static class TestModule extends AbstractModule {
		@Override
		protected void configure() {
			bind(MyService.class).to(MyServiceImpl.class);
			// ...
		}
	}


	@Inject
	public MyService service;

	@Test
	@GuiceModules(TestModule2.class)
	public void perTestSpecificModule() {
		// ...
	}

	@Test
	public void test() {
		// ...
	}
}
```
