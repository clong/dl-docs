# DetectionLab Documentation

This repo is used to make changes to the documentation hosted on https://detectionlab.network

Most page content is located in the `content/` directory. Please open a pull request for each requested change.


## Step by Step Instructions

Updating documentation is a great way to familiarize yourself with creating pull requests if you've never done it before! Here's some steps to get you started:

1. Create a fork of this repo by clicking the "fork" button in the upper right
2. You'll now have a fork located at `https://github.com/<your-github-username>/dl-docs/`
3. Visit that page and click the green "Code" button and copy the HTTPS link that is displayed to you
4. From a terminal, run `git clone <the link you just copied>`
5. Make changes to the .md files inside of the `content/` directory
6. Once you're done, commit those changes by running `git commit -a` 
7. Checkout a branch with a brief name explaining the change `git checkout -b fix_outdated_splunk_index`
8. Run `git push`
9. Visit https://github.com/clong/dl-docs and a button should now be present to let you open a pull request!
