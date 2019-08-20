#=========================================================================
#
#  Copyright Niels Dekker, LKEB, Leiden University Medical Center
#
#  Licensed under the Apache License, Version 2.0 (the "License");
#  you may not use this file except in compliance with the License.
#  You may obtain a copy of the License at
#
#        http://www.apache.org/licenses/LICENSE-2.0.txt
#
#  Unless required by applicable law or agreed to in writing, software
#  distributed under the License is distributed on an "AS IS" BASIS,
#  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
#  See the License for the specific language governing permissions and
#  limitations under the License.
#
#=========================================================================

# The version that appears to be installed on azure vmImage 'vs2017-win2016'
cmake_minimum_required( VERSION 3.14.5 )

project (HelloQt)

message(STATUS "[${PROJECT_NAME}] CMAKE_VERSION = ${CMAKE_VERSION}")
message(STATUS "[${PROJECT_NAME}] CMAKE_GENERATOR = ${CMAKE_GENERATOR}")

if(CMAKE_CONFIGURATION_TYPES)
  set(CMAKE_CONFIGURATION_TYPES Debug Release)
else()
  set(CMAKE_BUILD_TYPE Release)
endif()

set(CMAKE_VERBOSE_MAKEFILE ON)

# Require (at least) the Qt version provided by vcpkg.
find_package(Qt5 5.12.3 COMPONENTS Core Gui REQUIRED)

add_executable(${PROJECT_NAME}
	${PROJECT_NAME}.cpp)

target_link_libraries(${PROJECT_NAME}
	Qt5::Core
	Qt5::Gui
)