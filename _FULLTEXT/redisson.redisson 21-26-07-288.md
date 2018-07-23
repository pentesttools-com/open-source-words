redisson redis based in memory data grid for java state of the art redis client quick start documentation javadocs changelog code examples faqs support chat redisson pro based on high performance async and lock free java redis client and netty framework stable release version release date jdk version compatibility completionstage support projectreactor version compatibility 3 7 3 27 06 2018 1 8 1 9 1 10 yes 3 1 x 2 12 3 27 06 2018 1 6 1 7 1 8 1 9 1 10 android no 2 0 8 features replicated servers mode also supports aws elasticache and azure redis cache automatic master server change discovery cluster servers mode also supports aws elasticache cluster and azure redis cache automatic master and slave servers discovery automatic status and topology update automatic slots change discovery sentinel servers mode automatic master slave and sentinel servers discovery automatic status and topology update master with slave servers mode single server mode thread safe implementation reactive streams api asynchronous api asynchronous connection pool lua scripting distributed objects object holder binary stream holder geospatial holder bitset atomiclong atomicdouble publishsubscribe bloom filter hyperloglog distributed collections map multimap set list sortedset scoredsortedset lexsortedset queue deque blocking queue bounded blocking queue blocking deque delayed queue priority queue priority deque distributed locks and synchronizers lock fairlock multilock redlock readwritelock semaphore permitexpirablesemaphore countdownlatch distributed services remote service live object service executor service scheduler service mapreduce service spring framework spring cache implementation spring transaction api implementation hibernate cache implementation transactions api xa transaction api implementation jcache api jsr 107 implementation tomcat session manager implementation spring session implementation redis pipelining command batches supports android platform supports auto reconnection supports failed to send command auto retry supports osgi supports ssl supports many popular codecs jackson json avro smile cbor msgpack kryo amazon ion fst lz4 snappy and jdk serialization with over 1800 unit tests used by success stories moving from hazelcast to redis datorama distributed locking with redis migration from hazelcast contaazul migrating from coherence to redis rci quick start maven jdk 1 8 compatible dependency groupid org redisson groupid artifactid redisson artifactid version 3 7 3 version dependency jdk 1 6 compatible dependency groupid org redisson groupid artifactid redisson artifactid version 2 12 3 version dependency gradle jdk 1 8 compatible compile org redisson redisson 3 7 3 jdk 1 6 compatible compile org redisson redisson 2 12 3 java java 1 create config object config 2 create redisson instance redissonclient redisson redisson create config 3 get object you need rmap map redisson getmap mymap rlock lock redisson getlock mylock rexecutorservice executor redisson getexecutorservice myexecutorservice over 30 different objects and services downloads redisson 3 7 3 redisson node 3 7 3 redisson 2 12 3 redisson node 2 12 3 faqs q i saw a redistimeoutexception what does it mean what shall i do can redisson team fix it q i saw a com fasterxml jackson databind jsonmappingexception during deserialization process can you fix it q there were too many quotes appeared in the redis cli console output how do i fix it q when do i need to shut down a redisson instance at the end of each request or the end of the life of a thread q in mapcache setcache springcache jcache i have set an expiry time to an entry why is it still there when it should be disappeared q how can i perform pipelining transaction through redisson q is redisson thread safe can i share an instance of it between different threads q can i use different encoder decoders for different tasks supported by yourkit is kindly supporting this open source project with its full featured java profiler yourkit llc is the creator of innovative and intelligent tools for profiling java and net applications take a look at yourkits leading software products yourkit java profiler and yourkit net profiler