# chigadziko

Wildfly && jUnit is's very simple with chigadziko

## What is chigaziko?

Chigadziko is a factory for EJB bean fields with support of base EJB functionality - bean creating and PersistenceContext initializing
Chigaziko is very useful for testing EJB modules with jUnit
Using Chigaziko you can work with EJB using methos of POJO.

## Sample of chigaziko using

@EJB
private SomeClassManager someClassManager;

@Before
void tearUp() {
  // Initialize all EJB fields and create Persistence context
  Chigaziko.makeEJBContext(this);
}

@After
void tearUp() {
  // Clear all EJB context fcreatet in before method
  Chigaziko.shutdownEJBContext(this);
}

@Test
void t000test1() {
  // Here all EJB field are initialized, you can use and test them
  someClassManager.someVoid();
}


