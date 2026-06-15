---

author: "Dushyant Basson"
categories:
- uncategorized
date: "2020-09-04"
slug: "deploying-a-template-in-visual-studio"
tags:
- api
- archicad
- graphisoft
- visual-studio
title: "Deploying a template in Visual Studio"
---



I had to use MS Visual Studio to work with Graphisoft's Archicad API. The API kit installs a template in Visual Studio, though the references to the libraries and header files in the template have a relative path specially for the example projects that come with the kit. That required editing the path to the referenced files in the template in order to use it for projects stored in locations other than the Examples directory of the API kit.



The templates in Visual Studio are stored in the form of a ZIP file. Though the decompressed template can be customised by editing, duplicating the template with customisations is not as simple as unzipping the template, edit the files and re-zip as a new template to be available in Visual Studio. From what I gathered, Visual Studio 2017 onwards, the templates are not simply scanned for in their directories. They are instead required to 'provide some "manifest" file storing the template's location' ([Ref](https://docs.microsoft.com/en-us/visualstudio/extensibility/creating-custom-project-and-item-templates?view=vs-2019)).



This is a compilation of the steps to generate a usable template in Visual Studio 2017 (community) using broadly gathered info, not describing the mechanism or the structure of the template.



An existing project-template can be found in `%userprofile%/Documents/Visual Studio 2017/Templates/ProjectTemplates` Duplicate the ZIP file of the template, extract and customise it. Re-compress it into a ZIP file.



(It seems some tags need to be defined in the \<Template Data\> section in the .vstemplate file, for compatibility with v2019. [Ref.](https://docs.microsoft.com/en-us/visualstudio/ide/template-tags?view=vs-2019#built-in-tags))



In order to deploy this customised template, a [VSIX project template](https://docs.microsoft.com/en-us/visualstudio/extensibility/vsix-project-template?view=vs-2019) is needed. The VSIX project template becomes available in the New Project dialog box (search vsix) after installing the Visual Studio SDK. To install Visual Studio SDK, run the Visual Studio installer and install 'Visual Studio extension development' workload. [Ref.](https://docs.microsoft.com/en-us/visualstudio/extensibility/visual-studio-sdk?view=vs-2019)



After the VSIX project template is available in the New Project dialog in Visual Studio:



- Create a new VSIX project using the Visual C# VSIX template.

- Right-click on the VSIX project in the Solution Explorer and select 'Set as Startup Project'.

- Browse the Solution Explorer for a source.extension.vsixmanifest file. Double-click to open it, and a form opens up.

- In the 'Assets' section, select New. In the 'Add New Asset' dialog box, select Type as Microsoft.VisualStudio.ProjectTemplate and Source as 'File on filesystem'. Browse and select the ZIP file of the template. The template ZIP file should now be listed in the Solution Explorer under ProjectTemplates.

- Build the project for release version. Browse to the _bin > Release_ directory of the VSIX project, and run the .vsix file that was generated to install the template.

- The template should now be available in the New Project dialog box after restarting Visual Studio. Search for the template by the <Name> specified in <TemplateData> of the .vstemplate file.



Hope this helps someone. Share your thoughts / suggestions please. Thanks.
