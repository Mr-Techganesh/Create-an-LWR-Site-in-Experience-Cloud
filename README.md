# The Hive Foundation Community Resource Management Tool

## Use Case
The Hive Foundation focuses on community impact programs to help people experiencing poverty or homelessness. Their leadership are deeply troubled by the rise of adolescent mental health challenges and want to help communities respond. The first step in their plan is to build a tool that anyone in a community can use to contribute local resources, events, and support opportunities. Their vision is that these tools can be deployed in communities around the world to aggregate resources and help build more resilient and well-resourced communities.

## Business Requirements
Your first step in helping the foundation is to complete the build of a screen flow. Eventually, this flow will live on the Hive Foundation’s website, but for now it will be used by internal staff. When it’s live, website visitors will be able to enter key information about a variety of community resources.

## Creating Flow in Flow Builder

### Screen 1: Resource Management
You’ve done quite a bit of work in setting up the Resource Management flow and are looking forward to adding and modifying screens for users to input data. Begin by creating a welcome screen situated between the flow Start and the first Assignment element. Name the first screen Resource Management and add a description of your choosing.

- Add welcome text to display a welcome message to users; we suggest something like Welcome to the Hive Foundation community! Thanks for contributing. with API Name Welcome.
- Add the Hive Foundation logo under the display text. The logo is already in your special org with the API Name Hive_Foundation_Logo. Set the API Name to hive_logo with alt text Hive Logo and image width to 80%.
- Add a Radio Buttons component with label text How may we help you today? with API Name resource_input. Make this Radio Button component required and do not let users select multiple options. Define the first choice as {!StartNewResourceRequest} to allow the user to create a new resource, and define the second choice as {!EditExistingResourceRequest} to allow the user to update an existing resource.
- Add a Text component to capture the Resource Name for returning users, with API Name it_resource_name. The resource name should only be visible when the user indicates they are working with an existing resource.
- Add the Dynamic Flow Progress custom component to the top of the screen above the Welcome message. Give it the API Name Dynamic_Progress_Start. In configuring this component, set the list of steps to the {!Flow_Steps} variable. On this first screen, set the Current Step to Step 1. Set the Indicator Type to Bar.

### Update Assignment and S2 New Resource Request elements
After completing the initial screen, modify the Assignment element labeled Assign Resource Name in the Resource Management flow, and update the two inputs to values entered in Screen 1: Resource Management.
Next up is the S2 New Resource Request screen. This screen is partially configured. Add more features to the screen so the user can input the needed information. Add a Lookup component with API Name lu_account, which should look up to the Account object that is on the Resource record.
- Add a Multi-Select Picklist component to indicate the target audience, with API Name mspl_target_audience. Set the Choice input to {!choiceset_resource_audience_type}.
- Add a picklist component for Resource Type with API Name pl_resource_type. Set the Choice input to {!choiceset_resource_type}.
- Add a section called Event Details with section API Name Event_Details. This section should only be visible if the resource type is Event.
- Add components to capture the start date and time (API Name idt_Start_Date_and_Time) and end date and time (API Name idt_End_Date_and_Time) for events. Include validation to ensure the end date is after the start date.

### Assign resource details
Next, configure the Assign Resource Details element in the Resource Management flow. Update the following variables to reflect the value captured in the corresponding component from the S2 New Resource Request screen.
- Target Audience
- Resource Type
- Start Date
- End Date
- Account

### Screen 3: S3 Edit Resource Request
Replace the placeholder text with appropriate field values in the following elements with the matching field values using the record variable resource.
- “Add Primary Contact Name field value”
- “Add Type field value”
- “Add Account name field value”
Modify the Email component to restrict editing to the Email field.
Configure two fields on the S3 Edit Resource Request screen to display default values from the Resource record the user is referencing. Update the default value of the Resource Title and Description input fields to display the value from that Resource record.

# Display a Flow on a Page Outside Your Salesforce Org

## Learning Objectives
After completing this unit, you’ll be able to:
- Describe use cases for displaying a flow outside your Salesforce org.
- List the types of Experience Builder pages.
- Create a new Experience Builder page and add a flow to it.

For users logging into a Salesforce org, we've got lots of options: Lightning pages, flow actions, and the utility bar. But what if you want to open up access to the flow to folks without a Salesforce license?

Lucky for us, we can add flows to our org's Experience Builder sites. Putting a flow on a site is just as easy as putting a flow on a Lightning page. Here are some examples of flows that are perfect for sites built on Experience Builder, whether the site is geared toward customers, partners, employees, or some other group altogether:
- Surveys
- Registration forms
- Interest forms
- Quote generators, such as for a car they're selling


## Experience Builder Pages
One of the first tasks for creating an Experience Builder site is selecting the template. Each template comes with a specific set of Experience Builder pages. That said, all Experience Builder pages fall into one of these categories:
- My Pages: The standard pages that you create. (The object pages that you create appear under Objects.)
- Template Pages: The default pages that come with the site template.
- Objects: The pages of the objects in your site, which include the object’s record detail, list, and related list pages.
- Generic Record Pages: These generic pages are used to display record information for a Salesforce object when custom object pages don’t exist.
- Login Pages: The default login pages that come with the site template.

## Add Your Flow to an Experience Builder Page
It takes a lot of planning and know-how to set up a site for users. But if we don't have a site, we can't exactly show you how to add a flow to one. So let’s breeze through creating a site, and then add a flow. We’ve learned about elements and components used for building flows, but within Experience Builder, Flow is, itself, a component. Read on and you’ll see.

1. Enable Digital Experiences for your Trailhead Playground. (If it's already enabled, skip ahead to step 2.)
   a. From Setup, enter digital in the Quick Find box, then click Settings under Digital Experiences.
   b. Click Enable Digital Experiences.
   c. Enter a domain name, make sure it's available, and then save your changes.
   
2. Create a site.
   a. You should have been redirected to the All Sites page in Setup. If not, or if you skipped step 1, enter Digital Experiences in the Quick Find box, and select All Sites.
   b. Click New.
   c. Select the Customer Service template, then click Get Started.
   d. Enter a name for the site and click Create.

3. Now that we've built a fresh site, let's add our flow to its home page.
   a. From the My Workspaces page, click Builder to open Experience Builder.
   b. In the top-left corner, click Components to open the Components pane.
   c. Search for Flow to find the right component. Drag Flow onto the Experience Builder page.
   d. Make sure that the component displays the right flow. In the properties pane for Flow, select Hello World.

## Test Your Flow
All done! Let's see how the flow works in a real live site.

1. In the top-right corner of the Experience Builder, click Publish, and then Publish again. If this is the first time you're publishing this site, it'll take a few minutes. While you wait for the confirmation email, why not grab a cup of coffee?
   - Normally, you'd preview the site before you publish it, but the Flow component doesn't display the flow in design or preview mode. That’s a fail-safe to prevent the flow from performing an action (like creating a bunch of records) before the first screen.

2. In the “Site Published Successfully” confirmation email, click the link.

3. If you aren't logged in, under the login fields, click Are you an employee? Login here. If you need to enter the username and password for your Trailhead Playground, check out the Get Your Trailhead Playground Username and Password unit of the Trailhead Playground Management module, which shows you how to find them.

That's it! Your flow is now live, and available to site users.

![Screenshot 2024-03-11 193149](https://github.com/Mr-Techganesh/Lightning-web-Runtime-LWR-Project/assets/117075085/06a6ef1f-5a88-4ec7-90e6-5211affbf23d)

## Project Live Link

 Check out: https://sns-c-dev-ed.develop.my.site.com/hive


