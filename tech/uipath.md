% UiPath Doc

<link id="linkstyle" rel="stylesheet" href="markdown.css"/>

# Intro #

## Main Types ##

* Sequences
  suitable to linear processes, enabling you to smoothly go from on activity to another, without cluttering 
  your project.

* Flowcharts
  suitable to a more complex business logic, enabling you to integrate decisions and connect activities in a more
  diverse manner, through multiple branching logic operators.

* State Machine
  suitable for very large projects. They use a finite number of states in their execution which are triggered by
  a condition or activity.

* Global Error

## Data Types ##

* GenericValue Variables
  The GenericValue variable is a type of variable that can store any kind of data, including text, numbers,
  dates, and arrays, and is particular to UiPath Studio.

# Recording #
* The recorders are a set of wizards that enable you to quickly create simple automations skeletons which you
  can later modify.
* There are four types of recorders: Basic, Desktop, Web and Citrix.
* There are two types of recording methods: step by step and automatic.

## Basic Recording ##
  * Basic and Desktop are almost identical in behavior, 
    + Recordable: Left Clicks on: buttons, checkboxes, dropdowns, etc
    + Non-Recordable: Keyboard shortcuts, Modifier keys, Right click, Mouse hover, etc
    + Manual-Recording: Keyboard shortcuts, Modifier keys, Right click, Mouse hover, etc
      Get Text, Find elements and images, Copy to clipboard.
  * Feature
    + Actions are self-contained
    + Simpler workflow
    - Can cause interference

## Desktop Recording ##
  * Feature
    + Actions are contained inside an AttachWindow component
    + No interference issue
    - More complex workflow

## Web Recording ##

## Citrix Recording ##
Citrix is for recording virtual machines, VNC, and of course Citrix environments.

# Advanced UI Interaction Introduction #

There are two types of User Interface interactions that can appear:
* Input: insert data into application, and Output reading data from an application.
* Ouput: reading data from an application.

In this module we will cover three main input methods:
* Hardware Events(default)
* Send Windows Messages
* Simulate(type/click)

and also three main output methods:
* FullText
* Native
* OCR

Things you will learn:
* How to set up the three Input methods and differences between them.
* How to use the Screen Scraping Wizard.
* How to set up the three Output methods and differences between them.
* How to use Data Scraping Wizard.

## Screen Scraping ##

### When to use screen scraping ###
* for bigger block text
* information behind complex UI
* you need exact word position on screen

## Data Scraping ##

## Selectors ##

### Full Selector ###
* Have top-level element.
* Basic Recorder uses full-selectors.

### Partial Selector ###
* Does not have top-level element.
* Desktop Recorder uses partial-selectors.

### wildcards ###

### AnchorBase Selector ###

### Relative Selector ###


## Image and Text automation ##

### Basic Citrix Automation ###

### Keyboard Automation ###

### Retrieve Infomation ###
* Scrape Relative
* 

## Excel and DataTables ##
* How to read from an Excel file using the Read Range Activity
* How to operate with a datatable
* How to filter a defined table in Excel
* How to use Append Range

### Activity ###

App -> Integration -> Excel
* Reading/Writing Excel file
* Iterate Excel file

#### Use Excel app/Direct access ####
* Requires MS Office Excel installed
* Multiple processes can use the same file
* Visible read-time changes

* Does not require MS Office Excel
* Only one process can use the file
* Works only for xlsex format

#### Tips ####

Notice that 'Add Headers' option.

## PDF ##

* NOTE: 打开"引用XObject对象模式"

* How to use 'Read PDF' Activity
* How to use 'Read PDF with OCR' Activity
* How to use anchors to get data from a field inside a PDF

### Extracting data from PDF ###
* 'Read PDF'
* 'Read PDF with OCR'
* 'Screen Scraping'

### Extracting a single piece of data ###

### Anchor base activity ###
* Use 'Find element' or 'Find Image' for anchor
* Use 'Get Text' to retrieve the data


## eMail Automation ##
* How to use the dedicated Email activities
* How to send and receive messages
* How to filter and download attachments from an email
* How to use message templates

## Debugging and Exception Handling ##
* How to use debug features
* How to sync with applications using Find Element or Element Exists
* How to trycatch activity works and how to use it 

### Timing and sync issue ###
* Element Exist
* Find Element
* Wait Element Vanish

## Project Orgnization ##

* How to use Invoke Workflow Activity
* How to orgnise your project in a clean and efficient way

### Aim ###

* Reliable
* Efficient
* Maintainable
* Extensible

### Best Practies ###

* Pick an appropriate layout for each workflow
* Break the whole process in smaller workflows
* Use exception handling
* Make your workflows readable
* Keep it clean

Reference To: RTF[^2]

-------------------------------------------------------------------------------

# Learn more about UiPath #

## Introduction ##

## About Licensing ##

## Ther User Interface ##

## Keyboard Shortcuts ##

## About Updating ##

## About Automation Projects ##

## Introduction to Automation Debugging ##

## Managing Activities Packages ##

## Reusing Automations Library ##

## Installing the Chrome Extension ##

## Installing the firefox Extension ##

## Connecting Your Project to a Source Control System ##

## Activities Guide ##

-------------------------------------------------------------------------------

# L1 UIPath fundamental #
* Studio
作为后台创建Process，并发布到Orchestrator上。
* Robot
分成两种不同的定义
    + Attanded Robot 一般用于人机互动的流程，手动触发。
    + Unattanded Robot 常封装于VM上，在Orchestrator上设置固定启动时间定点触发。

* Orchestrator
使用Studio开发完一个流程后，一般会将其发布到一个Orchestrator。

# workflow #

* Sequences
* Flowcart
* StateMahine

## 变量 ##

### 属性 ###

* Name
* Type
  + Boolean
  + Int32
  + String
  + Object
  + Generic Value 
    泛型
  + Array Of [T]
  + Browse for Types 
    类型库
* Scope
* Default

## 输入输出 ##

## Selector ##

#### Selector Editor####

### 通配符 ###

### UI Explorer ###

## Excel和数据表自动化 ##

### Excel类Activity ###
* Excel下的所有activities都必须包含在Excel application scope这个activity内才可以使用
* 默认会打开Excel进程，可以通过设置Visible属性选择不显示Excel文档。

### Workbook类Activity ###
* 在与Excel类文档相比中，推荐使用Workbook类Activity。因为不需要打开Excel进程。

### 基本操作 ###

* Read Cell, Write Cell
* Read Range, Write Range
* Read Column, Read Row
* Append Range

### 实例 ###

1. Read Range读取表格
2. Build Data Table根据需要创建一个数据表
3. For Each Row
4. Write Range

### Lookup Data Table ###

* Input
  + LookupValue
  可以通过Read Range读取，LookupValue是我们要查找的值，可以是常量也可以是变量
* Lookup Column
  + Column
  + ColumnIndex
  + ColumnName
* Output
  + RowIndex
  + CellValue
* Target Column
  Target Column是我们要查找的值在查找区域所在行对应的列，类似Lookup Column，对应列也可以通过一样的方法指定，这边就不赘述了。

## 键盘, 鼠标UI交互 ##

### Click, Double Click ###
目标可以通过 Indicate On Screen功能自动生成，该功能试图标识指定区域中的UI元素，并为其生成Selector(UiPath基础篇 - 初识Selector)。如果这对指定目标不起作用，则可能需要手动干预（UiPath基础篇 - Selector进阶1）。

### Hover ###
模拟鼠标在指定目标上悬停。

### Type into, Type Secure Text ###

### Send Hotkey ###

### Set Focus ###

## 文本自动化 ##

在某些特殊情况下，UI元素无法通过标准方法进行标识，这时候文本自动化相关的activity则能够根据它们包含的文本，去识别按钮、复选框和其它UI元素。

### Click Text, Hover Text ###

### Get Full Text ###

### Text Exist ###

### Extract Structured Data ###

## 图像自动化 ##

### Click Image, Hover Image ###

### Find Image ###

等待指定图像出现后再执行下一步activity。

### Image Exist ###

用于验证屏幕上是否存在某个指定图像。它会返回一个布尔变量，该变量声明是否找到了该图像。
和Find Image相似，能够根据给定的图像是否显示，或者通过将其用作Retry Scope activity的条件，为在循环中执行某些操作来做出决策。

### On Image Apprear ###

### On Image Vanish ###

## PDF ##

### Read PDF Text ###


-------------------------------------------------------------------------------

# L2 Orchestrator #

## Tutorial Outline ##

* How to deploy and trigger a process
  + Publishing a UiPath workflow
  + Creating an environment
* How to provision a Robot
* Further understanding of versioning
* Scheduling jobs
* How the job queue works, handling pending jobs, canceling and terminating jobs
  + The difference between canceling and terminating a job
* How to monitor all Robots registered to the Orchestrator through the log
  + How levels of error messages are communicated
* What are assets?
  + Storing variables in the Orchestrator
  + Specifying which robots will use which stored assets
  + Storing credentials in the Orchestrator
* Orchestrator queues
  + Using queues to work with lists of items that are handled by multiple Robots
  + Statuses of items in queues
  + How to add items to queues and how to get transaction items
  + How to track progress of transaction items
* Job input and output arguments

## Steps ##

### Publish a project ###

### Register your robot to Orchestrator ###
1. Add Machine
2. Create Robot
3. Connect Orchestrator from windows Robots settings

### Publishing your first process ###
1. Create a new Environment
2. Create a process

### Scheduling jobs ###

### Publishing the same process with new version ###

* If the robot instance is not connected to Orchestrator, the package has to be uploaded manually.
  1. Publish a package in Studio. The package is sent to a local folder.
  2. Goto the Packages section in Orchestrator and click on Upload. 
  3. Browse for the .nupkg file, which is saved in C:\ProgramData\UiPath\Packages by default.
  4. Click Upload to add the package to Orchestrator.

### Other ways to run a process ###

* Manually triggering a robot from the Assistant interface.
  1. Goto Robot Interface in the System Tray and click on the UI icon.
  2. Find the process, which should be available.
  3. Click the Play button next to the process.

### Schedules ###

'Stop Job after' and 'Disable Schdule at' from Actions tab.
The 'Stop Job after' property features the same the same two options - 'Stop & Kill'

### Assets and credentials practice ###

### Queues ###

Queues are very powerful tools in Orchestrator. They help you divide the work between multiple
robots, without having to keep track of complicated rules. As the name suggests, the transaction
items in a queue are processed in chronological order, with the exceptions mentioned in the
tutorial video.

To create a queue:
1. Under the 'Queues' section in Orchestrator, click the 'Add' button.
2. Click the 'Name' field and enter a name, such as 'Queue1'.
3. In the 'Max # of retries' section, type 3.

The create the first workflow, we will use an activity call 'Add Queue Item'.
1. Read the excel file as Data Table
2. Drag and drop an 'Add Queue Item' and place it in a 'For each row' activity.
3. The 'QueueName' field in the 'Properties' panel enables you to link this activity with a queue in
   Orchestrator.
4. The 'ItemInfomation' field is where the values of the transaction item can be added.

The second automation project features two relevant activities: 'Get transaction item' and 
'Set transaction status'. The first one requests an item from the queue. The second one notifies 
Orchestrator that a specific transaction item has been processed - successfully or not.
1. Create a new Sequence in Studio. Name it 'ProcessTransactions'.
2. 'Get Transaction Item' activity, fill in the 'QueueName' field by entering the previously created queue.

* Application Exception
  A transaction item that fails with an Application Exception is placed back in the queue and tried
  either at a later time or by a differenct Robot.

### Input and Output Arguments ###
Sets arguments at the scenirio:
1. Process -> Parameter
2. Jobs -> Parameter

-------------------------------------------------------------------------------
 
# L3 Advanced Training #




-------------------------------------------------------------------------------

# Computer Vision #

Computer Vision is a feature that allows our Robots to 'see' the screen and visually identify all the elements,
ranther than relying on selector or images. It is an algorithm that enables human-like recognition os user
interfaces, using a mix of AI, OCR, text fuzzy-matching, and an anchoring system to tie it all together.

[AI Computer Vision Activity Pack](https://activities.uipath.com/docs/about-the-ai-computer-vision-activities-pack)

-------------------------------------------------------------------------------

# UiPath Studio 2018.4 Updates #

## Global Exception Hanlder ##

[Global Exception Handler](https://studio.uipath.com/docs/global-exception-handler#section-example-of-using-the-global-exception-handler)

## Citrix ##

[Citrix](https://studio.uipath.com/docs/about-native-citrix-automation)

## Save As Template ##

As the name states, it’s a Save As Template feature which allows you to save a Process or a Library as a template
that you can later re-use in your automation projects.

[Save As Template](https://studio.uipath.com/docs/project-templates)

## Repo Browser ##

[VCS](https://studio.uipath.com/docs/about-version-control)

## Process Libraries ##

### Steps ###

1. Creating Process Libraries

2. Importing Process Libraries

3. Customizing Process Libraries

4. Reusable Components

5. Making Private options

6. Libraries Publishing Errors

## Dark Theme ##

[Dark Theme](https://activities.uipath.com/docs/applying-themes-to-custom-activities)

# UiPath Orchestrator 2018.4 Updates #

## Webhooks ##

[Webhooks](https://orchestrator.uipath.com/docs/about-webhooks)
[Webhook.site](https://webhook.site/)

## Development Robot Decoupling ##

Two types of development robots
1. Standard Robots:
   - Installed along with Studio
   - Can be used on a single machine

2. Floating Robots:
   - Enable RPA developers to do their work seamlessly

-------------------------------------------------------------------------------

# UiPath 2019.4 Updates #

## UiPath 2019.4 Studio Updates ##

* Package Management Bundle
  - Libraries and Activities per Tenant
  -
  [Manageing Activities](https://studio.uipath.com/docs/managing-activities-packages)

* GIT Integration & Workflow Diff
  [File Diff](https://studio.uipath.com/docs/using-file-diff#section-comparing-workflow-versions)

* SOAP and Swagger Libraries
  - What is it?
  Studio can now generate activies from **SOAP and Swagger** based REST services through the New Service
  wizard available for libraries. The service is added to the library's dependency tree and from there on,
  you can add activies to your library from the Activities panel.
  - Why do you need it?
  Instead of spending long hours of **constructing HTTP Requests**, you can incorporate this new, simple and
  extremely useful addition of Services to the Library projects, which can be integrated seemingly.
  As an example you can ease the process of creating new workflows, by simply loading services, turning them
  into activies and then feeding all necessary variables, instead of creating a long .json string, filled with
  quotes escaped by more quotes from scratch.

  [SOAP and Swagger](https://studio.uipath.com/docs/loading-web-services-in-libraries)

* Edit Settings

* Go!Marketplace Studio Integration

* Debugging in 2019.4

## UiPath 2019.4 Orchestrator Updates ##

* Real Time Monitoring
* Libraries and Activies per Tenant
* Universal Blob Storage

* Encryption Key per Tenant

* Orchestrator Mobile App

* UiPath Recording


## UiPath 2019.4 Activities ##

* Intelligent OCR - Document Processing Framework

* Regex Builder

* IBM Lotus Notes

* Support for variables in 'Selectors'

## UiPath 2019.4 Driver ##

* Native Citrix Support

* Native RPD Support

* Better Browsing Support

[^2]: (Rich Text Format) A document format from Microsoft for encoding text and graphics. It was adapted from IBM's DCA format and supports ANSI, IBM PC and Macintosh character sets. The RTF format is used as a source document for Windows Help files and other Microsoft products.

| keybindings  |                function |
|:-------------|------------------------:|
| Ctrl-k       |         create variable |
| Ctrl-m       |  create input parameter |
| Ctrl-Shift-m | create output parameter |
|              |                         |