readme in chinese a scalable crawler framework it covers the whole lifecycle of crawler downloading url management content extraction and persistent it can simplify the development of a specific crawler features simple core with high flexibility simple api for html extracting annotation with pojo to customize a crawler no configuration multi thread and distribution support easy to be integrated install add dependencies to your pom xml xml dependency groupid us codecraft groupid artifactid webmagic core artifactid version 0 7 3 version dependency dependency groupid us codecraft groupid artifactid webmagic extension artifactid version 0 7 3 version dependency webmagic use slf4j with slf4j log4j12 implementation if you customized your slf4j implementation please exclude slf4j log4j12 xml exclusions exclusion groupid org slf4j groupid artifactid slf4j log4j12 artifactid exclusion exclusions get started first crawler write a class implements pageprocessor for example i wrote a crawler of github repository infomation java public class githubrepopageprocessor implements pageprocessor private site site site me setretrytimes 3 setsleeptime 1000 override public void process page page page addtargetrequests page gethtml links regex https github\\ com \\w \\w all page putfield author page geturl regex https github\\ com \\w tostring page putfield name page gethtml xpath h1 class public strong a text tostring if page getresultitems get name null skip this page page setskip true page putfield readme page gethtml xpath div id readme tidytext override public site getsite return site public static void main string args spider create new githubrepopageprocessor addurl https github com code4craft thread 5 run page addtargetrequests links add urls for crawling you can also use annotation way java targeturl https github com \w \w helpurl https github com \w public class githubrepo extractby value h1 class public strong a text notnull true private string name extractbyurl https github\\ com \\w private string author extractby div id readme tidytext private string readme public static void main string args oospider create site me setsleeptime 1000 new consolepagemodelpipeline githubrepo class addurl https github com code4craft thread 5 run docs and samples documents http webmagic io docs the architecture of webmagic refered to scrapy there are more examples in webmagic samples package lisence lisenced under apache 2 0 lisence thanks to write webmagic i refered to the projects below scrapy a crawler framework in python http scrapy org spiderman another crawler framework in java http git oschina net l weiwei spiderman mail list https groups google com forum forum webmagic java http list qq com cgi bin qf invite id 023a01f505246785f77c5a5a9aff4e57ab20fcdde871e988 qq group 373225642 542327088 related project gather platform a web console based on webmagic for spider configuration and management