# chigadziko

Wildfly && jUnit is very simple with chigadziko

## What is chigadziko?

Chigadziko is a factory for EJB bean fields with support of base EJB functionality - bean creating and PersistenceContext initializing
Chigaziko is very useful for testing EJB modules with jUnit
Using Chigaziko you can work with EJB using methos of POJO.

## Sample of chigadziko using


    @EJB
    private SomeClassManager someClassManager;

    @Before
    void tearUp() {
      // Initialize all EJB fields and create Persistence context
      Chigadziko.makeEJBContext(this);
    }

    @After
    void tearUp() {
      // Clear all EJB context fcreatet in before method
      Chigadziko.shutdownEJBContext(this);
    }

    @Test
    void t000test1() {
      // Here all EJB field are initialized, you can use and test them
      someClassManager.someVoid();
    }
    
 (*and don't forget do define all persistence context units for modules purposed to be tested in persistence.xml*)

## Why not Arquillian and similar suits?

Arquillian is purposed to test full .ear application using jUnit. But testing of the application it is an integration test, not unit test. If you need unit testing for your module you can not use Arquillian and similar tools.
But Chigadziko help make unit testing easy and transparent.


