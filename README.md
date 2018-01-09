# Documentation for apptuit.ai
[![Travis](https://img.shields.io/travis/ApptuitAI/documentation.svg)](https://travis-ci.org/ApptuitAI/documentation/)
[![Gemnasium](https://img.shields.io/gemnasium/ApptuitAI/documentation.svg)](https://gemnasium.com/github.com/ApptuitAI/documentation)
[![license](https://img.shields.io/github/license/ApptuitAI/documentation.svg)](https://github.com/ApptuitAI/documentation/blob/master/LICENSE)

Welcome to the GitHub repo for our documentation.
Our docs are completely open source and we deeply appreciate contributions from our community!
Feel free to send us pull requests and/or file issues.

If you are looking to browse/read the documentation visit [our documentation  website](https://apptuitai.github.io/documentation/).

## Logging issues

We have made it easy to log an issue from any page. You could also log an issue from our [GitHub issues page](https://github.com/ApptuitAI/documentation/issues)

#### Recommended types of issues
Please log an issue/bug in these situations:
- If you don't see something that should be in the docs.
- If you see something incorrect or confusing in the docs.

#### Forums vs bugs
We have a user community to address usage questions and discuss feature requests. Please use the forums instead of logging a bug in these situations:
- If your problem is a general question about how to configure or use ApptuitAI.
- If you have an idea for a new feature or behavior change in a specific aspect
  of ApptuitAI, or have found a bug in part of ApptuitAI.

## Contributing

We value your contributions from our user community. These could be something simple like typos, grammar errors, bug fixes or more involved like Restructuring or documentation for a brand new feature.

#### Make your first contribution!

For simple changes, you can contribute by just clicking the edit button on the page and submitting your change.

For more involved changes, you can clone the repo to your desktop, submit your changes by following these steps:
- Fork our `master` branch and clone the fork to your desktop
- Make your changes locally
- Preview the changes on GitHub once you commit and push your changes
- When you are ready to contribute your changes back, make a pull request back to `ApptuitAI/documentation/master`
- Once your pull request is approved, it will be merged into our master and your changes will be automatically available on our documentation site

## Running locally

If you would like to preview your changes locally before committing to GitHub, you can run the site locally.

#### Initial Setup
You need `Ruby` and `gem` before starting. Install Ruby 2.4 by following [these instructions](https://www.ruby-lang.org/en/documentation/installation/). Then:

```bash
# install bundler
gem install bundler

# clone the project
git clone https://github.com/ApptuitAI/documentation.git
cd documentation

# install required packages
bundle install
```

#### Potential setup issues
 * If you see the following error on windows:
 > Could not open library 'libcurl.dll': The specified module could not be found.  

  * Download [libcurl.zip](https://curl.haxx.se/gknw.net/7.40.0/dist-w64/curl-7.40.0-winssl-sspi-zlib-static-bin-w64.zip)
  * Extract `libcurl.dll` file from the downloaded zip and save it into your `ruby\bin` directory
 *  

#### Running the documentation server

Launch the documentation server using the following command:
 ```bash
 # run jekyll with dependencies
 bundle exec jekyll serve
 ```

Once the server is ready, you will see the following message:
```
Server address: http://127.0.0.1:4000/
Server running... press ctrl-c to stop.
```

You can now access the documentation site locally by pointing your browser to https://localhost:4000

#### Validating your local changes
Once you have previewed your changes in the browser, run the following commands to verify all your changes before committing:
```bash
# generate all content
bundle exec jekyll build

# verify there are no broken links
bundle exec htmlproofer ./_site
```


## LICENSE

```
Copyright 2017 Agilx, Inc.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
