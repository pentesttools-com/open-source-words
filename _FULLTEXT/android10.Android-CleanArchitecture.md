Android-CleanArchitecture New version available written in Kotlin: Architecting Android… Reloaded Introduction This is a sample app that is part of a blog post I have written about how to architect android application using the Uncle Bobs clean architecture approach. Architecting Android…The clean way? Architecting Android…The evolution Tasting Dagger 2 on Android Clean Architecture…Dynamic Parameters in Use Cases Demo video of this sample Clean architecture Architectural approach Architectural reactive approach Local Development Here are some useful Gradle/adb commands for executing this example: ./gradlew clean build - Build the entire example and execute unit and integration tests plus lint check. ./gradlew installDebug - Install the debug apk on the current connected device. ./gradlew runUnitTests - Execute domain and data layer tests (both unit and integration). ./gradlew runAcceptanceTests - Execute espresso and instrumentation acceptance tests. Discussions Refer to the issues section: https://github.com/android10/Android-CleanArchitecture/issues Code style Here you can download and install the java codestyle. https://github.com/android10/java-code-styles License Copyright 2018 Fernando Cejas Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0 Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.