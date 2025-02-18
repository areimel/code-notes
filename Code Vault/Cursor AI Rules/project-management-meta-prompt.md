*Pre-Prompt Notes*:

You should start out with writing up a 1 or 2 paragraph summary of the project you want to build, including any libraries or services you want to use or know you'll need. Then, take that prompt and feed it into ChatGPT to have it give you a more detailed explanation of how you'll build the project, have it explain any parts you don't understand, and tell you what additional libraries you'll need. Make sure you double check any critical libraries to ensure they're being used correctly.

This meta-prompt relies on a set of markdown files: 
- CURSOR_PROJECT_OVERVIEW.md
	- Written by dev
- CURSOR_PROJECT_PLAN.md
	- AI-generated, static file
	- Written at the beginning of the project and acts as and idealized/optimized master plan that should be the main reference for the AI.
- CURSOR_PROJECT_TIMELINE.md
	- AI-generated, gets updated with progress
	- Based on the CURSOR_PROJECT_PLAN file, this acts as a checklist of features and tasks that helps the AI keep track of what needs to be done and in what order.
- **CURSOR_PROJECT_SAVEPOINT**.md
	- AI-generated, updated at the end of each coding session
	- You should request this file be made when stepping away from the project and you want Cursor to create a meta-prompt that directs Cursor to access and review its Composer memory and allow you to pick back up where you left off.
- CURSOR-PROJECT-TESTS.md
	- AI-generated, gets updated with progress
	- Cursor should use this file to keep track of the tests for different features, how the tests work and what libraries they use, and what tests are passing and failing.
	- Cursor should use this file both to keep track of all tests throughout the course of the project, and also as a reference when building new tests so that consistent testing methods are used.
- CURSOR-PROJECT-REVIEW.md

---
## Prompts
### Create Plan
> I am building a new project from scratch, and I'd like you to help me get started. I have provided a detailed overview in the file @CURSOR_PROJECT_OVERVIEW.md. First, I want you to review @CURSOR_PROJECT_OVERVIEW.md, and then I want you to develop a plan of how we will build this project and break it down into major sections. I want you to create a new markdown file called 'CURSOR_PROJECT_PLAN' and I want you to store your detailed plan there. You should write and format CURSOR_PROJECT_PLAN in a way where it will serve as an ideal and optimized prompt for Cursor's Composer function to use as the master plan for the project. It should contain the entire plan for the project, from the initial setup to publishing it. It shouldn't be updated by Cursor after it is initially written, so it doesn't get altered by accident.

### Create Timeline
> Now that you've created @CURSOR_PROJECT_PLAN, I want you to create a new markdown file based on it called 'CURSOR_PROJECT_TIMELINE' where you keep track of our progress on the project and what features are complete, in progress, or not started yet. This file should also be used to check what feature should be worked on next and keep both the AI and the developer on-track with building the project correctly.

### Create Save Point
> I'm taking a break, and I want to ensure continuity for what we're currently working on for the next Composer instance I open. I want you to do this by creating a new markdown file called CURSOR_PROJECT_SAVEPOINT. This file should detail what we're currently working on, along with the last 3 features we worked on and any issues we're currently running into, and it should make use of Cursor's '@' symbol commands such as `@Summarized Composers` and `@Recent Changes` to have the new Composer instance access previous discussions and updates. You should write and format this as an idealized meta-prompt for Cursor to maintain continuity across Composer instances, and you should reference the @Cursor (https://docs.cursor.com/get-started/welcome) official docs to make full use of Cursor's features when writing the SAVEPOINT meta-prompt. The meta-prompt should be detailed and robust enough to maintain continuity across different Cursor installations on different machines.

### Keep Track Of Tests
> Every time we build and finalize a new set of unit tests, I want you to make a log of it in a markdown file called CURSOR-PROJECT-TESTS, and organize it by feature. This file should serve as a way to track what tests are present in the project, how they are built, how you run them, and what tests are passing or failing. It should serve as a reference when running tests later in the project, to ensure all tests are remembered. It should also serve as a reference when building new tests, to ensure that they are built consistently and use the same libraries when applicable. 







---

Original versions:


I'd like for you to help me get started with a new, fresh project. I've written out a detailed overview of how I want to build this project in @CURSOR_PROJECT_OVERVIEW.md . I want you to first review these instructions, and then I want you to develop a plan of how we will build this project and break it down into major sections. I want you to create a new markdown file called 'CURSOR_PROJECT_PLAN' and I want you to store your detailed plan there. I also want you to creat a new markdown file called 'CURSOR_PROJECT_TIMELINE' where you keep track of where we are in the project and what features are complete, in progress, or not started yet.


# autoscreenshot - cli tool

**Project summary**: I want to build a CLI tool called 'autoscreenshot' that takes screenshots of web pages using a headless browser. I would also like to publish this tool as an npm package so that others can use it.

## Build Process

I want this CLI tool to be Node.js-based, and have it work seamlessly on Windows, Mac, and Linux. I want the tools to be built using Commander.js to provide a helpful, verbose interface for the tool that walks the user through the tool's options. I'd also like it to be built using the Chalk library to provide colors and styling to the interface. I want the tool to use the 'fs' and 'path' libraries to handle files and filesystem operations. Finally, the tool should use the Puppeteer library to handle the headless browser. If there are any other libraries I'll need to handle major features I request, please let me know.

I would also like the tool to use a `settings.json` file to control certain features like device size, file format, delay options, and other features that can be easily controlled and modified by simple string and number values. Users should also be able to set up their own custom preset arguments using this file, so they can set up preset options they frequently use.

I would also like for the tool to check for and ask to download include any required libraries it needs, such as Chromium, during its initial installation.

## Features 

- The CLI tool should accept a URL as an input parameter. Running the CLI tool should look like `autoscreenshot https://test.com`.
- When the user only inputs a URL, the tool should then walk the user through a brief set of options for their screenshot, but the user should also be able to skip options by including them as arguments in their initial command input. The options I want available are:
	- 'screenshot type': This should be multiple choice with the options 'full page' or 'initial viewport'.
		- The 'full page' option should take a screenshot of the entire length of the page that is seamlessly stitched together.
		- The 'initial viewport' option should take a screenshot of just what is shown within the viewport when the page load - typically referred to as "above the fold" in marketing.
	- 'device size': This should be a multiple choice option, allowing the user to select a preset size for the screenshot. The choices should be 'desktop', 'laptop', 'tablet', 'phone'. 
		- There should also be an 'all devices' option that takes a screenshot on every device size. 
		- This option should be configurable in the `settings.json` file, allowing the user to add additional sizes such as `largeDisplay: '2400px'`, or adjust and rename the default sizes.
	- 'delay': This option should let the user set a delay before the headless browser takes a screenshot, to account for the page and any external plugins to load. The user should have the option to either input a number in seconds, including a decimal point, such as `1.5`, or to use their default delay setting, which can be configured in the `settings.json` file. 
	- 'format': This option should let the user choose between .png and .jpg files. The default should be .jpg, to save on file size, but this should be able to be configured in the `settings.json` file.
		- There should also be an option in `settings.json` to skip over this option in the interface and always use the default option.
	- 'file destination': this option should control where the screenshot gets saved to. It should let the user choose between their default preferred location, the folder the user is currently in, or let them choose to provide a location.
		- This option should be configurable in the `settings.json` file, allowing the user to change the default file destination. It should also let them choose whether they want to skip this option in the interface and always use the default option. 

## File Handling

On first installation, the autoscreenshot tool should ask the user to provide a folder location for their default file destination. It should give the user instructions to make it a new folder that is somewhere easy to find, such as on their desktop. The `settings.json` file should be located in this folder, and the CLI tool should create it there upon initial installation. 

## Modes

The autoscreenshot CLI tool should have multiple modes to allow it to handle different use cases:
- Normal mode: this is the normal default mode as described by this outline so far - the CLI tool takes one or more screenshots of a webpage and briefly walks the user through the screenshot options.
- Batch mode: this mode should take a series of screenshots based on a json or csv file provided by the user. The user activates the batch mode option by typing `autoscreenshot batch`. The CLI interface then displays a brief description of what batch mode is, and asks the user for the location of the json or csv file containing the URLs they want to screenshot, and then walk them through the usual settings that will then be applied to the entire batch. 
	- For json files, an argument string can be set at the beginning of the file to handle the screenshot settings.
	- The tools should save the entire batch of screenshots to its own folder, named something like `autoscreenshot-batch-date-time`
- Accessibility mode: This mode should apply various color filters or blurring to simulate what users with visual differences or disabilities would see.

## Help

If no URL or alternate mode is provided, such as if the user just types in `autoscreenshot`, I want the CLI tool to display a helpful set of instructions that explains the different options, their corresponding arguments, the different modes, and the locations of the current default file destination folder and the `settings.json` file.