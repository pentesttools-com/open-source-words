angularstrap angularstrap is a set of native directives that enables seamless integration of bootstrap 3 0 into your angularjs 1 2 app with no external dependency except the bootstrap css styles angularstrap is lighter and faster than ever as it does leverage the power of nganimate from angularjs 1 2 angularstrap is tested against the latest patch release of the 1 2 1 3 1 4 and 1 5 branches if you dont want to use nganimate you will have to include a tiny nganimate mock looking for maintainers were currently looking for aspiring maintainers to tackle issues and pull requests i mgcrea have not worked on any angular js v1 codebase for more than a year now for me its time to move on if you have an ongoing project depending on angularstrap and would like to become a contributor please chime in on issue 2256 documentation and examples check the documentation and changelog communication if you need help use stack overflow tag angular strap if youd like to ask a general question use stack overflow if you found a bug open an issue if you have a feature request open an issue if you want to contribute submit a pull request quick start install angularstrap with bower bash bower install angular strap save include the required libraries in your index html html script src bower components angular angular js script script src bower components angular animate angular animate js script script src bower components angular strap dist angular strap min js script script src bower components angular strap dist angular strap tpl min js script inject the mgcrea ngstrap module into your app js angular module myapp nganimate mgcrea ngstrap developers clone the repo git clone git github com mgcrea angular strap git download the latest release or install with bower bower install angular strap save you will need to have bower installed globally into your node environment bash npm install g bower angularstrap is tested with karma against the latest stable release of angularjs angularstrap uses gulp 4 0 you must use the local gulp instance with npm bin gulp for it to work or use an alias bash npm install bower install cd docs bower install cd npm test or npm run test watch you can build the latest version using gulp bash npm bin gulp build you can quickly hack around the docs with bash npm bin gulp serve you can browse to http localhost 9090 dev html to work on a specific directive contributing please submit all pull requests the against master branch if your pull request contains javascript patches or features you should include relevant unit tests please check the contributing guidelines for more details thanks authors olivier louvignes http olouv com http github com mgcrea copyright and license the mit license copyright c 2012 – 2015 olivier louvignes permission is hereby granted free of charge to any person obtaining a copy of this software and associated documentation files the software to deal in the software without restriction including without limitation the rights to use copy modify merge publish distribute sublicense and or sell copies of the software and to permit persons to whom the software is furnished to do so subject to the following conditions the above copyright notice and this permission notice shall be included in all copies or substantial portions of the software the software is provided as is without warranty of any kind express or implied including but not limited to the warranties of merchantability fitness for a particular purpose and noninfringement in no event shall the authors or copyright holders be liable for any claim damages or other liability whether in an action of contract tort or otherwise arising from out of or in connection with the software or the use or other dealings in the software