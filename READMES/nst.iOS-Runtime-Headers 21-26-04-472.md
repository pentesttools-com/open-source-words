dynamically generated ios headers here are ios objective c headers as derived from runtime introspection the headers were generated using runtimebrowser for iphone search you can search the headers with github search https github com search type code q repo nst ios runtime headers hack diffs you can compare versions based on their tags see the tags page git difftool 6 0 6 1 sample usage you can use the headers this way nsbundle b nsbundle bundlewithpath system library privateframeworks ftservices framework bool success b load class ftdevicesupport nsclassfromstring ftdevicesupport id si ftdevicesupport valueforkey sharedinstance nslog si valueforkey devicecolor timeline green public red private blue dylib the code to draw this picture is in https github com nst runtimebrowser tree master tools ios headers history nicolas seriot