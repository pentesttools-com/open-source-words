objectmapper objectmapper is a framework written in swift that makes it easy for you to convert your model objects classes and structs to and from json features the basics mapping nested objects custom transformations subclassing generic objects mapping context objectmapper alamofire objectmapper realm projects using objectmapper to do contributing installation features mapping json to objects mapping objects to json nested objects stand alone in arrays or in dictionaries custom transformations during mapping struct support immutable support the basics to support mapping a class or struct just needs to implement the mappable protocol which includes the following functions swift init map map mutating func mapping map map objectmapper uses the operator to define how each member variable maps to and from json swift class user mappable var username string var age int var weight double var array any var dictionary string any var bestfriend user nested user object var friends user array of users var birthday date required init map map mappable func mapping map map username map username age map age weight map weight array map arr dictionary map dict bestfriend map best friend friends map friends birthday map birthday datetransform struct temperature mappable var celsius double var fahrenheit double init map map mutating func mapping map map celsius map celsius fahrenheit map fahrenheit once your class implements mappable objectmapper allows you to easily convert to and from json convert a json string to a model object swift let user user jsonstring jsonstring convert a model object to a json string swift let jsonstring user tojsonstring prettyprint true alternatively the mapper swift class can also be used to accomplish the above it also provides extra functionality for other situations swift convert json string to model let user mapper user map jsonstring jsonstring create json string from model let jsonstring mapper tojsonstring user prettyprint true objectmapper can map classes composed of the following types int bool double float string rawrepresentable enums array any dictionary string any object t mappable array t mappable array array t mappable set t mappable dictionary string t mappable dictionary string array t mappable optionals of all the above implicitly unwrapped optionals of the above mappable protocol mutating func mapping map map this function is where all mapping definitions should go when parsing json this function is executed after successful object creation when generating json it is the only function that is called on the object init map map this failable initializer is used by objectmapper for object creation it can be used by developers to validate json prior to object serialization returning nil within the function will prevent the mapping from occuring you can inspect the json stored within the map object to do your validation swift required init map map check if a required name property exists within the json if map json name nil return nil staticmappable protocol staticmappable is an alternative to mappable it provides developers with a static function that is used by objectmapper for object initialization instead of init map map note staticmappable like mappable is a sub protocol of basemappable which is where the mapping map map function is defined static func objectformapping map map basemappable objectmapper uses this function to get objects to use for mapping developers should return an instance of an object that conforms to basemappable in this function this function can also be used to validate json prior to object serialization provide an existing cached object to be used for mapping return an object of another type which also conforms to basemappable to be used for mapping for instance you may inspect the json to infer the type of object that should be used for mapping see examples in classclustertests swift if you need to implemented objectmapper in an extension you will need to select this protocol instead of mappable immutablemappable protocol immutablemappable provides the ability to map immutable properties this is how immutablemappable differs from mappable immutablemappable mappable properties let id int let name string var id int var name string json model init map map throws id try map value id name try map value name mutating func mapping map map id map id name map name model json func mapping map map id map id name map name mutating func mapping map map id map id name map name initializing try user jsonstring jsonstring user jsonstring jsonstring init map map throws this throwable initializer is used to map immutable properties from the given map every immutable property should be initialized in this initializer this initializer throws an error when map fails to get a value for the given key map fails to transform a value using transform immutablemappable uses map value using method to get values from the map this method should be used with the try keyword as it is throwable optional properties can easily be handled using try swift init map map throws name try map value name throws an error when it fails createdat try map value createdat using datetransform throws an error when it fails updatedat try map value updatedat using datetransform optional posts try map value posts optional default value mutating func mapping map map this method is where the reverse transform is performed model to json since immutable properties can not be mapped with the operator developers have to define the reverse transform using the operator swift mutating func mapping map map name map name createdat map createdat datetransform updatedat map updatedat datetransform posts map posts easy mapping of nested objects objectmapper supports dot notation within keys for easy mapping of nested objects given the following json string json distance text 102 ft value 31 you can access the nested objects as follows swift func mapping map map distance map distance value nested keys also support accessing values from an array given a json response with an array of distances the value could be accessed as follows distance map distances 0 value if you have a key that contains you can individually disable the above feature as follows swift func mapping map map identifier map app identifier nested false when you have nested keys which contain you can pass the custom nested key delimiter as follows 629 swift func mapping map map appname map com myapp info com myapp name delimiter custom transforms objectmapper also supports custom transforms that convert values during the mapping process to use a transform simply create a tuple with map field name and the transform of your choice on the right side of the operator swift birthday map birthday datetransform the above transform will convert the json int value to an date when reading json and will convert the date to an int when converting objects to json you can easily create your own custom transforms by adopting and implementing the methods in the transformtype protocol swift public protocol transformtype associatedtype object associatedtype json func transformfromjson value any object func transformtojson value object json transformof in a lot of situations you can use the built in transform class transformof to quickly perform a desired transformation transformof is initialized with two types and two closures the types define what the transform is converting to and from and the closures perform the actual transformation for example if you want to transform a json string value to an int you could use transformof as follows swift let transform transformof fromjson value string int in transform value from string to int return int value tojson value int string in transform value from int to string if let value value return string value return nil id map id transform here is a more condensed version of the above swift id map id transformof fromjson int 0 tojson 0 map string 0 subclasses classes that implement the mappable protocol can easily be subclassed when subclassing mappable classes follow the structure below swift class base mappable var base string required init map map func mapping map map base map base class subclass base var sub string required init map map super init map override func mapping map map super mapping map sub map sub make sure your subclass implemenation calls the right initializers and mapping functions to also apply the mappings from your superclass generic objects objectmapper can handle classes with generic types as long as the generic type also conforms to mappable see the following example swift class result mappable var result t required init map map func mapping map map result map result let result mapper map json mapping context the map object which is passed around during mapping has an optional mapcontext object that is available for developers to use if they need to pass information around during mapping to take advantage of this feature simply create an object that implements mapcontext which is an empty protocol and pass it into mapper during initialization swift struct context mapcontext var importantmappinginfo info that i need during mapping class user mappable var name string required init map map func mapping map map if let context map context as context use context to make decisions about mapping let context context let user mapper context context map jsonstring objectmapper alamofire if you are using alamofire for networking and you want to convert your responses to swift objects you can use alamofireobjectmapper it is a simple alamofire extension that uses objectmapper to automatically map json response data to swift objects objectmapper realm objectmapper and realm can be used together simply follow the class structure below and you will be able to use objectmapper to generate your realm models swift class model object mappable dynamic var name required convenience init map map self init func mapping map map name map name if you want to serialize associated realmobjects you can use objectmapper realm it is a simple realm extension that serializes arbitrary json into realms list class to serialize swift string int double and bool arrays you can use objectmapperadditions realm itll wrap swift types into realmvalues that can be stored in realms list class note generating a json string of a realm object using objectmappers tojson function only works within a realm write transaction this is caused because objectmapper uses the inout flag in its mapping functions which are used both for serializing and deserializing realm detects the flag and forces the tojson function to be called within a write block even though the objects are not being modified projects using objectmapper xcode plugin for generating mappable and immutablemappable code json4swift supports generating immutablemappable structs online no plugins needed if you have a project that utilizes extends or provides tooling for objectmapper please submit a pr with a link to your project in this section of the readme to do improve error handling perhaps using throws class cluster documentation contributing contributions are very welcome 👍😃 before submitting any pull request please ensure you have run the included tests and they have passed if you are including new functionality please write test cases for it as well installation cocoapods objectmapper can be added to your project using cocoapods 0 36 or later by adding the following line to your podfile ruby pod objectmapper 3 3 carthage if youre using carthage you can add a dependency on objectmapper by adding it to your cartfile github hearst dd objectmapper 3 3 swift package manager to add objectmapper to a swift package manager based project add swift package url https github com hearst dd objectmapper git majorversion 3 minor 2 to your package swift files dependencies array submodule otherwise objectmapper can be added as a submodule add objectmapper as a submodule by opening the terminal cd ing into your top level project directory and entering the command git submodule add https github com hearst dd objectmapper git open the objectmapper folder and drag objectmapper xcodeproj into the file navigator of your app project in xcode navigate to the target configuration window by clicking on the blue project icon and selecting the application target under the targets heading in the sidebar ensure that the deployment target of objectmapper framework matches that of the application target in the tab bar at the top of that window open the build phases panel expand the target dependencies group and add objectmapper framework click on the button at the top left of the panel and select new copy files phase rename this new phase to copy frameworks set the destination to frameworks and add objectmapper framework