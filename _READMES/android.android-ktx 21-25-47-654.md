android ktx a set of kotlin extensions for android app development the goal of android ktx is to make android development with kotlin more concise pleasant and idiomatic by leveraging the features of the language such as extension functions properties lambdas named parameters and parameter defaults it is an explicit goal of this project to not add any new features to the existing android apis kotlin kotlin val uri uri parse myuristring kotlin with android ktx kotlin val uri myuristring touri kotlin kotlin sharedpreferences edit putboolean key value apply kotlin with android ktx kotlin sharedpreferences edit putboolean key value kotlin kotlin val pathdifference path mypath1 apply op mypath2 path op difference canvas apply val checkpoint save translate 0f 100f drawpath pathdifference mypaint restoretocount checkpoint kotlin with android ktx kotlin val pathdifference mypath1 mypath2 canvas withtranslation y 100f drawpath pathdifference mypaint kotlin kotlin view viewtreeobserver addonpredrawlistener object viewtreeobserver onpredrawlistener override fun onpredraw boolean viewtreeobserver removeonpredrawlistener this actiontobetriggered return true kotlin with android ktx kotlin view doonpredraw actiontobetriggered getting started to add android ktx to your project add the following to your app modules build gradle groovy repositories google dependencies implementation androidx core core ktx 1 0 0 alpha1 then in your kotlin files where youd like to use the extensions import the appropriate packages project status this project is currently in preview and we are seeking feedback from the community we encourage you to try android ktx so you can suggest ideas and report issues please see the how to contribute section if you would like to contribute during the preview period the android ktx apis may change at anytime when the project reaches a stable state we will update it to version 1 0 or later from that point forward we will be much more rigorous and careful about maintaining api compatibility this project does not currently cover the android support library or architecture components apis links api reference documentation issue tracker report a defect or feature request stackoverflow ask how to and why didnt it work type questions how to contribute we welcome your contributions to this project there are various ways to contribute reporting issues help improve the project by reporting issues that you find by filing a new issue at the android ktx issue tracker features suggestions you can also add feature suggestions by filing a new issue at the android ktx issue tracker documentation you can help by adding or improving existing documentation simply send us a pull request for us to consider your proposed changes bug fixes pull requests are welcome for minor bug fixes that do not involve any changes to existing api these changes should ideally be accompanied by a test case that would have otherwise failed without the fix new api or api changes pull requests for new apis or changes to existing apis are welcome but may require a bit of discussion consider creating an issue to discuss any changes before you implement the change before submitting if you are making an api change run gradlew updateapi and commit any changes in the api directory check that lint unit tests and code style enforcement all pass by running gradlew check check that instrumentation tests pass by starting an api 26 or newer emulator and running gradlew connectedcheck note first time contributors to a google or android project will be required to sign a cla license copyright 2018 the android open source project licensed under the apache license version 2 0 the license you may not use this file except in compliance with the license you may obtain a copy of the license at http www apache org licenses license 2 0 unless required by applicable law or agreed to in writing software distributed under the license is distributed on an as is basis without warranties or conditions of any kind either express or implied see the license for the specific language governing permissions and limitations under the license