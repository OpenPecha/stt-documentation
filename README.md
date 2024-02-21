# README

> **Note:** This readme template is based on one from the [Good Docs Project](https://thegooddocsproject.dev). You can find it and a guide to filling it out [here](https://gitlab.com/tgdp/templates/-/tree/main/readme). (_Erase this note after filling out the readme._)

<h1 align="center">
  <br>
  <a href="https://openpecha.org"><img src="https://avatars.githubusercontent.com/u/82142807?s=400&u=19e108a15566f3a1449bafb03b8dd706a72aebcd&v=4" alt="OpenPecha" width="150"></a>
  <br>
</h1>

## stt-documentation

## Owner(s)

- [@spsither](https://github.com/spsither)

## RFXs
Requests for work (RFWs) and requests for comments (RFCs) associated with this project:
* [RFW0125: Technical documentation about STT and TTS workflow for other developers ](https://github.com/OpenPecha/Requests/issues/363)
* [RFC0125: Technical documentation about STT and TTS workflow for other developers ](https://github.com/OpenPecha/Requests/issues/450)


* [RFW0112: Tracking STT and TTS models and creating documentation](https://github.com/OpenPecha/Requests/issues/362)
* [RFC0112: Tracking STT and TTS models and creating documentation](https://github.com/OpenPecha/Requests/issues/452)

## Table of contents
<p align="center">
  <a href="#project-description">Project description</a> •
  <a href="#who-this-project-is-for">Who this project is for</a> •
  <a href="#project-dependencies">Project dependencies</a> •
  <a href="#instructions-for-use">Instructions for use</a> •
  <a href="#contributing-guidelines">Contributing guidelines</a> •
  <a href="#additional-documentation">Additional documentation</a> •
  <a href="#how-to-get-help">How to get help</a> •
  <a href="#terms-of-use">Terms of use</a>
</p>
<hr>

## Project description

With stt-documentation you can browse through the documentation of the STT/TTS project in a one stop location without having to jump to several repos.

## Who this project is for
This project is intended for _target user_ who wants to _user objective_.
This project is intended for STT/TTS ML engineer and other ML engineers who wants to find specific details of the project. The Documents/home.md can also serve as a non technical overview of the project.

## Instructions for use
Get started with stt-documentation by going to the project Wiki and start browsing.

### Configure stt-documentation
This project uses GitHub repository action **secrets** to store the Personal Access Token (PAT) with repository permission to update the Wiki for this repo in GitHub actions.

1. Click on your user profile on the top right > `Settings` > `Developer settings` > `Personal access tokens` > `Tokens (classic)`
2. Click on Generate new token > make sure you give it `repo` scope 
3. Copy the token 
3. navigate to the [repo setting](https://github.com/OpenPecha/stt-documentation/settings)
4. Click on `Secrets and variables` > `Actions` > `New repository secret` 
5. Give it the name `GH_PERSONAL_ACCESS_TOKEN` and paste in the token from step 3 in Secret 


### Troubleshoot stt-documentation

<table>
  <tr>
   <td>
    Issue
   </td>
   <td>
    Solution
   </td>
  </tr>
  <tr>
   <td>
    PAT can expire
   </td>
   <td>
    Generate a new PAT using steps from Configure stt-documentation
   </td>
  </tr>
  <tr>
   <td>
    Documentation is unclear
   </td>
   <td>
    Ask repo owner to update it.
   </td>
  </tr>
</table>



## Contributing guidelines
If you'd like to help out, check out our [contributing guidelines](/CONTRIBUTING.md).


## Additional documentation

For more information:
* [GitHub Wiki](#https://docs.github.com/en/communities/documenting-your-project-with-wikis/about-wikis)


## How to get help
* File an issue.
* Email us at openpecha[at]gmail.com.
* Join our [discord](https://discord.com/invite/7GFpPFSTeA).


## Terms of use
_Project Name_ is licensed under the [MIT License](/LICENSE.md).
