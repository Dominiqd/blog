#SharePoint Online Synonyms
##Installation
1. Clone this repo
2. Open a command promp
3. Navigate to your folder
4. Execute
``
npm install
``

**Important**: You need to have webpack installed - ``npm install webpack -p``

##Compile the code
1. Run
``
webpack
``

##Creating the Synonyms List
Create a **Synonyms** (list name) SharePoint list with the following fields: **Title**, **Synonym** (multiple lines without markup), **DoubleUsage** (yes/no).

![Synonyms list](https://raw.githubusercontent.com/estruyf/blog/master/SPO-Synonyms/synonym-list.png "Synonyms list")

**Important**: insert the synonyms comma seperated like you can see in the screenshot.

###Info
By default if you create a thesaurus csv for SharePoint and want to make the synonym work in both ways, you have to specify multiple entries. 

```
Key,Synonym,Language   
HR,Human Resources
```

In this example, if you search on HR you will also get results for Human Resouces, but not the other way around. In order to get that working you have to specify it like this:

```
Key,Synonym,Language   
HR,Human Resources  
Human Resources,HR
```

The **DoubleUsage** field is in place to solve this issue so that you only have to specify one rule for each synony. So when the synonym should work in both ways, you set the field to **yes**. This also works when you enter multiple values in the Synonym field.

##Usage
1. Upload the file to your SharePoint Site.
2. Copy the file reference
3. On each search page, add a script editor web part
4. Specify the script reference in the web part ``<script src="enter-your-script-reference"></script>``
5. Edit the **Search Results Web Part** and click on **Change query**
6. Replace **{SearchBoxQuery}** with **{SynonymQuery}**
7. Go to the **Settings** tab and set the **loading behavior** to **Async option: Issue query from the browser**
8. Store these settings and publish the page

##Result
If I do a search query for **mp** on my environment, I should also get results for **managed property**.

![MP Search Query](/screenshots/example.png)

##Credits
Thank you [Mikael Svenson](https://twitter.com/mikaelsvenson) for creating the initial script.