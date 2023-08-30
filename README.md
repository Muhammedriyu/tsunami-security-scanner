Tsunami
build

Tsunami is a general purpose network security scanner with an extensible plugin system for detecting high severity vulnerabilities with high confidence.

To learn more about Tsunami, visit our documentation.

Tsunami relies heavily on its plugin system to provide basic scanning capabilities. All publicly available Tsunami plugins are hosted in a separate google/tsunami-security-scanner-plugins repository.

Current Status
Currently Tsunami is in 'pre-alpha' release for developer preview.
Tsunami project is currently under active development. Do expect major API changes in the future.
Quick Start
To quickly get started with Tsunami scans,

Traditional install
install the following required dependencies:

nmap >= 7.80
ncrack >= 0.7
start a vulnerable application that can be identified by Tsunami, e.g. an unauthenticated Jupyter Notebook server. The easiest way is to use a docker image:

docker run --name unauthenticated-jupyter-notebook -p 8888:8888 -d jupyter/base-notebook start-notebook.sh --NotebookApp.token=''
execute the following command:

bash -c "$(curl -sfL https://raw.githubusercontent.com/google/tsunami-security-scanner/master/quick_start.sh)"
The quick_start.sh script performs the following tasks:

Clone the google/tsunami-security-scanner and google/tsunami-security-scanner-plugins repos into $HOME/tsunami/repos directory.
Compile all Google Tsunami plugins and move all plugin jar files into $HOME/tsunami/plugins directory.
Compile the Tsunami scanner Fat Jar file and move it into $HOME/tsunami directory.
Move the tsunami.yaml example config into $HOME/tsunami directory.
Print example Tsunami command for scanning 127.0.0.1 using the previously generated artifacts.
Docker install
start a vulnerable application that can be identified by Tsunami, e.g. an unauthenticated Jupyter Notebook server. The easiest way is to use a docker image:

docker run --name unauthenticated-jupyter-notebook -p 8888:8888 -d jupyter/base-notebook start-notebook.sh --NotebookApp.token=''
build the docker image for Tsunami:

docker build -t tsunami .
run the Tsunami image. The logs can be saved to the host machine by mounting a volume:

docker run  --network="host" -v "$(pwd)/logs":/usr/tsunami/logs tsunami
Contributing
Read how to contribute to Tsunami.

License
Tsunami is released under the Apache 2.0 license.

Copyright 2019 Google Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
Disclaimers
Tsunami is not an official Google product.
