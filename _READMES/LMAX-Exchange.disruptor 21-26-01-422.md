lmax disruptor a high performance inter thread messaging library maintainer michael barker support google group documentation introduction getting started changelog 3 4 2 fix race condition in batcheventprocessor with 3 or more starting halting concurrently 3 4 1 fix race between run and halt on batcheventprocessor 3 4 0 drop support for jdk6 support jdk7 and above only add threadhints onspinwait to all busy spins within disruptor increase default sleep time for locksupport parknanos to prevent busy spinning 3 3 8 revert belt and braces waitstrategy signalling 3 3 7 add batch size to batchstartaware onbatchstart upgrade to newer versions of gradle checkstyle and junit deprecate classes methods for later release remove jmock and rewrite tests accordingly 3 3 6 support adding gating sequences before calling disruptor start fix minor concurrency race when dynamically adding sequences fix wrapping problem when adding work handlers to the disruptor 3 3 5 fix npe in timeoutblockingwaitstrategy when used with workprocessor add litetimeoutblockingwaitstrategy resignal any waiting threads when trying to publish to a full ring buffer 3 3 4 small build fixes and refactorings removed unused mutablelong class 3 3 3 support threadfactory in disruptor dsl make use of the executor deprecated 3 3 2 minor javadoc fixes example code and file renames additional generics for parametrised exceptionhandler 3 3 1 minor javadoc fixes example code and file renames make exceptionhandler type parametrised 3 3 0 inheritance based padding for ringbuffer and sequencers better dsl support for adding custom eventprocessors remove deprecated methods slightly breaking change experimental liteblockingwaitstrategy experimental eventpoller for polling for data instead of waiting 3 2 1 released 10 mar 2014 minor build and ide updates rewrite of performance tests to run without junit and separate queues in to their own tests remove old throttled performance test add performance tests for immutable message example add performance tests for off heap example remove old caliper tests remove some stray yield calls 3 2 0 released 13 aug 2013 fix performance bug in workprocessor with multiproducersequencer add eventrelease support to workprocessor experimental add pingponglatencytest switch to hdrhistogram for latency measurement 3 1 1 released 9 jul 2013 fix bug in workprocessor where consumers could get ahead of publishers 3 1 0 released 17 jun 2013 fix bug in disruptor dsl where some consumers wouldnt be included in the gating sequences add support for using the eventtranslator with batch publication support timeouts when shutting down the disruptor using the dsl 3 0 1 released 16 apr 2013 remove sequencer ensureavailable and move functionality into the processingsequencebarrier add get method and deprecate getpublished and getpreallocated from the ringbuffer add timeoutexception to sequencebarrier waitfor fix off by one bug in multiproducersequencer publish lo hi improve testing for sequencers 3 0 0 released 10 apr 2013 add remaining capacity to ringbuffer add batch publish methods to sequencer add dataprovider interface to decouple the ringbuffer and batcheventprocessor upgrade to gradle 1 5 3 0 0 beta5 released 08 apr 2013 make sequencer public 3 0 0 beta4 released 08 apr 2013 refactoring merge publisher back into sequencer and some of the gating sequence responsibilities up to the sequencer 3 0 0 beta3 released 20 feb 2013 significant javadoc updates thanks jason koch dsl support for workerpool small performance tweaks add timeouthandler and timeoutblockingwaitstrategy and support timeouts in batcheventprocessor 3 0 0 beta2 released 7 jan 2013 remove millisecond wakeup from blockingwaitstrategy add ringbuffer claimandgetpreallocated add ringbuffer ispublished 3 0 0 beta1 released 3 jan 2013 remove claim strategies and replace with publishers sequences remove pluggability of claim strategies introduce new multi producer publisher algorithm faster and more scalable introduce more flexible eventpublisher interface that allow for static definition of translators that can handle local values allow for dynamic addition of gating sequences to ring buffer default it to empty will allow messages to be sent and the ring buffer to wrap if there are no gating sequences defined remove batch writes to the ring buffer remove timeout read methods switch to gradle build and layout the source maven style api change remove ringbuffer get add ringbuffer getpreallocated for producers and ringbuffer getpublished for consumers change maven dependency group id to com lmax added phasedbackoffstrategy remove explicit claim forcepublish and supply a resetto method added better handling of cases when the gating sequence is ahead of the cursor value 2 10 3 released 22 aug 2012 bug fix race condition in sequencegroup when removing sequences and getting current value 2 10 2 released 21 aug 2012 bug fix potential race condition in blockingwaitstrategy bug fix set initial sequencegroup value to 1 issue 27 deprecate timeout methods that will be removed in version 3 2 10 1 6 june 2012 bug fix correct osgi metadata remove unnecessary code in wait strategies 2 10 13 may 2012 remove deprecated timeout methods added osgi metadata to jar file removed paddedatomiclong and use sequence in all places fix various generics warnings change sequence implementation to work around ibm jdk bug and improve performance by 10 add a remainingcapacity call to the sequencer class 2 9 8 apr 2012 deprecate timeout methods for publishing add trynext and trypublishevent for events that shouldnt block during delivery small performance enhancement for multithreadclaimstrategy 2 8 6 feb 2012 create new multithreadclaimstrategy that works between when threads are highly contended previous implementation is now called multithreadlowcontentionclaimstrategy fix for bug where eventprocessors werent being added as gating sequences to the ring buffer fix range tracking bug in histogram 2 7 1 21 dec 2011 artefacts made available via maven central repository groupid com googlecode disruptor artifactid disruptor see usingdisruptorinyourproject for details 2 7 12 nov 2011 changed construction api to allow user supplied claim and wait strategies added aggregateeventhandler to support multiple eventhandlers from a single batcheventprocessor support exception handling from lifecycleaware added timeout api calls for claiming a sequence when publishing use locksupport parknanos instead of thread sleep to reduce latency reworked performance tests to better support profiling and use linkedblockingqueue for comparison because it performs better on the latest processors minor bugfixes 2 6 introduced workerpool to allow the one time consumption of events by a worker in a pool of eventprocessors new internal implementation of sequencegroup which is lock free at all times and garbage free for get and set operations sequencebarrier now checks alert status on every call whether it is blocking or not added scripts in preparation for publishing binaries to maven repository 2 5 1 bugfix for supporting sequencereportingeventhandler from dsl issue 9 bugfix for multi threaded publishing to multiple ring buffers issue 10 change sequencebarrier to always check alert status before entering waitfor cycle previously this was only checked when the requested sequence was not available change claimstrategy to not spin when the buffer has no available capacity instead go straight to yielding to allow event processors to catch up 2 5 changed ringbuffer and publisher api so any mutable object can be placed in the ringbuffer without having to extend abstractevent added eventpublisher implementation to allow the publishing steps to be combined into one action disruptorwizard has been renamed to disruptor with added support for any subtype of eventprocessor introduced a new sequencer class that allows the disruptor to be applied to other data structures such as multiple arrays this can be a very useful pattern when multiple event processors work on the same event and you want to avoid false sharing the diamond for fizzbuzz is a good example of the issue it is also higher performance by avoiding the pointer indirection when arrays of primitives are used further increased performance and scalability by reducing false sharing added progressive backoff strategy to the multithreadedclaimstrategy to prevent publisher getting into the claim cycle when the buffer is full because of a slow eventprocessor significantly improved performance to waitstrategy option blocking introduced sequencegroup to allow dynamic registration of eventprocessors 2 0 2 rework of false sharing prevention which makes the performance much more predictable across all platforms special thanks to jeff hain for helping focus in on a solution 2 0 1 renaming mistake for publisheventatsequence should have been claimeventatsequence fixed bug in yieldingstrategy that was busy spinning more than yielding and introduced sleepingstrategy removed code duplication in unicast perf tests for expected result 2 0 0 new api to reflect naming changes producer publisher entry event consumer eventprocessor consumerbarrier dependencybarrier producerbarrier has been incorporated into the ringbuffer for ease of use disruptorwizard integrated for fluent api dependency graph construction rework of sequence tracking to avoid false sharing on java 7 plus avoid mega morphic calls to make better use of the instruction cache reduced usage of memory barriers where possible waitstrategy yielding initially spins for a short period to reduce latency major performance improvement giving more than a 2x increase for throughput across most use cases 1 2 2 producerbarrier change to yield after busy spinning for a while this may help the situation when the the number of producers exceeds the number of cores 1 2 1 bug fix for setting the sequence in the forcefillproducerbarrier code syntax tidy up 1 2 0 bug fix for regression introduced inlining multi thread producer commit tracking code this was a critical bug for the multi threaded producer scenario added new producerbarrier method for claiming a batch of sequences this feature can give a significant throughput increase 1 1 0 off by one regression bug in producerbarrier introduced in 1 0 9 clarified the algorithm for initial cursor value in the claimstrategy 1 0 9 added apache 2 0 licence and comments small performance improvements to producers barriers and batchconsumer 1 0 8 bugfix for batchconsumer sequence update when using sequencetrackinghandler to ensure sequence is always updated at the end of a batch regardless 1 0 7 factored out lifecycleaware interface to allowing consumers handlers to be notified when their thread starts and shuts down 1 0 6 cache minimum consumer sequence in producer barriers this helps make the performance more predictable on nehalem processors and greater on earlier core 2 processors 1 0 5 removed entry interface all entries must now extend abstractentry made setsequence package private on abstractentry for encapsulation