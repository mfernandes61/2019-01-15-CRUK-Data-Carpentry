---
layout: workshop      # DON'T CHANGE THIS.
carpentry: "dc"    # what kind of Carpentry (must be either "lc" or "dc" or "swc")
venue: "The Francis Crick Institute"        # brief name of host site without address (e.g., "Euphoric State University")
address: "Training Room, The Francis Crick Institute, 1 Midland Road, London NW1 1AT"      # full street address of workshop (e.g., "Room A, 123 Forth Street, Blimingen, Euphoria")
country: "gb"      # lowercase two-letter ISO country code such as "fr" (see https://en.wikipedia.org/wiki/ISO_3166-1)
language: "en"     # lowercase two-letter ISO language code such as "fr" (see https://en.wikipedia.org/wiki/ISO_639-1)
latlng: "51.236270,-0.612650"       # decimal latitude and longitude of workshop venue (e.g., "41.7901128,-87.6007318" - use http://www.latlong.net/)
humandate: "Nov 29-30, 2018"    # human-readable dates for the workshop (e.g., "Feb 17-18, 2020")
humantime: "9:30 - 17:30"    # human-readable times for the workshop (e.g., "9:00 am - 4:30 pm")
startdate: 2018-11-29      # machine-readable start date for the workshop in YYYY-MM-DD format like 2015-01-01
enddate: 2018-11-30        # machine-readable end date for the workshop in YYYY-MM-DD format like 2015-01-02
instructor: [ "Rocio T. Martinez Nunez","Adrian Baez-Ortega,  Mark Fernandes"] # boxed, comma-separated list of instructors' names as strings, like ["Kay McNulty", "Betty Jennings", "Betty Snyder"]
helper: []     # boxed, comma-separated list of helpers' names, like ["Marlyn Wescoff", "Fran Bilas", "Ruth Lichterman"]
email: ["Gabriella Rustici <gr231@cam.ac.uk>"]    # boxed, comma-separated list of contact email addresses for the host, lead instructor, or whoever else is handling questions, like ["marlyn.wescoff@example.org", "fran.bilas@example.org", "ruth.lichterman@example.org"]
collaborative_notes:  https://pad.carpentries.org/2018-11-29-Crick-London   # optional: URL for the workshop collaborative notes, e.g. an Etherpad or Google Docs document
eventbrite:           # optional: alphanumeric key for Eventbrite registration, e.g., "1234567890AB" (if Eventbrite is being used)
---

{% comment %} See instructions in the comments below for how to edit specific sections of this workshop template. {% endcomment %}

{% comment %}
  HEADER

  Edit the values in the block above to be appropriate for your workshop.
  If the value is not 'true', 'false', 'null', or a number, please use
  double quotation marks around the value, unless specified otherwise.
  And run 'make workshop-check' *before* committing to make sure that changes are good.
{% endcomment %}

{% comment %}
  EVENTBRITE

  This block includes the Eventbrite registration widget if
  'eventbrite' has been set in the header.  You can delete it if you
  are not using Eventbrite, or leave it in, since it will not be
  displayed if the 'eventbrite' field in the header is not set.
{% endcomment %}
{% if page.eventbrite %}
<iframe
  src="https://www.eventbrite.com/tickets-external?eid={{page.eventbrite}}&ref=etckt"
  frameborder="0"
  width="100%"
  height="248px"
  scrolling="auto">
</iframe>
{% endif %}

<h2 id="general">General Information</h2>

{% comment %}
  INTRODUCTION

  Edit the general explanatory paragraph below if you want to change
  the pitch.
{% endcomment %}
{% if page.carpentry == "swc" %}
  {% include sc/intro.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/intro.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/intro.html %}
{% endif %}

{% comment %}
  AUDIENCE

  Explain who your audience is.  (In particular, tell readers if the
  workshop is only open to people from a particular institution.
{% endcomment %}
{% if page.carpentry == "swc" %}
  {% include sc/who.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/who.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/who.html %}
{% endif %}

{% comment %}
  LOCATION

  This block displays the address and links to maps showing directions
  if the latitude and longitude of the workshop have been set.  You
  can use http://itouchmap.com/latlong.html to find the lat/long of an
  address.
{% endcomment %}
{% if page.latlng %}
<p id="where">
  <strong>Where:</strong>
  {{page.address}}.
  Get directions with
  <a href="//www.openstreetmap.org/?mlat={{page.latlng | replace:',','&mlon='}}&zoom=16">OpenStreetMap</a>
  or
  <a href="//maps.google.com/maps?q={{page.latlng}}">Google Maps</a>.
</p>
{% endif %}

{% comment %}
  DATE

  This block displays the date and links to Google Calendar.
{% endcomment %}
{% if page.humandate %}
<p id="when">
  <strong>When:</strong>
  {{page.humandate}}.
  {% include workshop_calendar.html %}
</p>
{% endif %}

{% comment %}
  SPECIAL REQUIREMENTS

  Modify the block below if there are any special requirements.
{% endcomment %}
<p id="requirements">
  <strong>Requirements:</strong> 
 Participants should bring their own laptop with a
  Mac, Linux, or Windows operating system (not a tablet, Chromebook, etc.) 
  that they have administrative privileges
  on. They should have a few specific software packages installed (listed
  <a href="#setup">below</a>). 
(Those without a laptop should arrange to borrow one from the Crick IT helpdesk).
They are also required to abide by
  {% if page.carpentry == "swc" %}
  Software Carpentry's
  {% elsif page.carpentry == "dc" %}
  Data Carpentry's
  {% elsif page.carpentry == "lc" %}
  Library Carpentry's
  {% endif %}
  <a href="{{site.swc_site}}/conduct.html">Code of Conduct</a>.
</p>

{% comment %}
  ACCESSIBILITY

  Modify the block below if there are any barriers to accessibility or
  special instructions.
{% endcomment %}
<p id="accessibility">
  <strong>Accessibility:</strong> We are committed to making this workshop
  accessible to everybody. 
  Please get in touch (using contact details below) if you have any special 
  requirements.
<p>
  Materials will be provided in advance of the workshop and
  large-print handouts are available if needed by notifying the
  organizers in advance.  If we can help making learning easier for
  you (e.g. sign-language interpreters, lactation facilities) please
  get in touch and we will attempt to provide them.
</p>

{% comment %}
  CONTACT EMAIL ADDRESS

  Display the contact email address set in the configuration file.
{% endcomment %}
<p id="contact">
  <strong>Contact</strong>:
  Please email
  {% if page.email %}
    {% for email in page.email %}
      {% if forloop.last and page.email.size > 1 %}
        or
      {% else %}
        {% unless forloop.first %}
        ,
        {% endunless %}
      {% endif %}
      <a href='mailto:{{email}}'>{{email}}</a>
    {% endfor %}
  {% else %}
    to-be-announced
  {% endif %}
  for more information.
</p>

<hr/>

{% comment %}
  SCHEDULE

  Show the workshop's schedule.  Edit the items and times in the table
  to match your plans.  You may also want to change 'Day 1' and 'Day
  2' to be actual dates or days of the week.
{% endcomment %}

{% comment %} DO NOT EDIT SURVEY LINKS {% endcomment %}

<p><em>Surveys</em></p>
{% if page.carpentry == "swc" %} 
<p>Please be sure to complete these surveys before and after the workshop.</p>
(% comment %) <p><a href="{{ site.swc_pre_survey }}{{ site.github.project_title }}">Pre-workshop Survey</a></p>
<p><a href="{{ site.swc_post_survey }}{{ site.github.project_title }}">Post-workshop Survey</a></p>
{% elsif page.carpentry == "dc" %}
  <p><b>Please be sure to complete this survey after the workshop:</b> 
  <a href="https://www.surveymonkey.co.uk/r/SFZXXWD">Cambridge training survey</a></p>

  <p>We would also appreciate if you filled in these surveys for the Data Carpentry community:</p>
  <p><a href="{{ site.dc_pre_survey }}{{ site.github.project_title }}">Data carpentry pre-workshop Survey</a></p>
  <p><a href="{{ site.dc_post_survey }}{{ site.github.project_title }}">Data carpentry post-workshop Survey</a></p>
{% elsif page.carpentry == "lc" %}
<p>Ask your instructor about pre- and post-workshop Survey details.</p>
{% endif %}

<hr/>

{% comment %}
  Collaborative Notes

  If you want to use an Etherpad, go to

      http://pad.software-carpentry.org/YYYY-MM-DD-site

  where 'YYYY-MM-DD-site' is the identifier for your workshop,
  e.g., '2015-06-10-esu'.
{% endcomment %}
{% if page.collaborative_notes %}
<p id="collaborative_notes">
  We will use this <a href="{{page.collaborative_notes}}">collaborative document</a> for chatting, taking notes, and sharing URLs and bits of code.
</p>
{% endif %}
<h2>Course Overview</h2>
<img src="assets/img/Data_carpentry_overview_fig.png" alt="overview" width="800"/>

<h2 id="schedule">Schedule</h2>
<a href="https://bioinformatics-core-shared-training.github.io/2018-11-29-Crick-London//timetable">Timetable</a>.  
<h3>Day 1</h3>

<h4>Data organization in spreadsheets ( )</h4>

<p>
  <H2>Data files for the lesson are available 
	  <a href="https://ndownloader.figshare.com/files/2252083">here</a>.</H2>
</p>

<ol>
  <li><a href="http://www.datacarpentry.org/spreadsheet-ecology-lesson/00-intro/">Introduction</a> (18 mins)</li>
  <li><a href="http://www.datacarpentry.org/spreadsheet-ecology-lesson/01-format-data/">Formatting data</a> (35 mins)</li>
  <li><a href="http://www.datacarpentry.org/spreadsheet-ecology-lesson/02-common-mistakes/">Common formatting problems</a> (20 mins)</li>
  <li><a href="http://www.datacarpentry.org/spreadsheet-ecology-lesson/03-dates-as-data/">Dates as data</a> (13 mins)</li>
  <li><a href="http://www.datacarpentry.org/spreadsheet-ecology-lesson/04-quality-control/">Quality control</a> (20 mins)</li>
  <li><a href="http://www.datacarpentry.org/spreadsheet-ecology-lesson/05-exporting-data/">Exporting data</a> (10 mins)</li>
</ol>

<h4>Data cleaning with OpenRefine ( )</h4>

<p>
  <H2>Data files for the lesson are available 
	  <a href="https://ndownloader.figshare.com/files/7823341">here</a></H2>.
</p>

<ol>
  <li><a href="http://www.datacarpentry.org/OpenRefine-ecology-lesson/00-getting-started/">Introduction</a> (10 mins)</li>
  <li><a href="http://www.datacarpentry.org/OpenRefine-ecology-lesson/01-working-with-openrefine/">Basics of OpenRefine</a> (35 mins)</li>
  <li><a href="http://www.datacarpentry.org/OpenRefine-ecology-lesson/02-filter-exclude-sort/">Filtering and sorting</a> (20 mins)</li>
  <li><a href="http://www.datacarpentry.org/OpenRefine-ecology-lesson/03-numbers/">Examining numeric data</a> (20 mins)</li>
  <li><a href="http://www.datacarpentry.org/OpenRefine-ecology-lesson/04-scripts/">Generating scripts</a> (15 mins)</li>
  <li><a href="http://www.datacarpentry.org/OpenRefine-ecology-lesson/05-save-export/">Exporting data</a> (15 mins)</li>
  <li><a href="http://www.datacarpentry.org/OpenRefine-ecology-lesson/06-resources/">Other resources</a> (10 mins)</li>  
</ol>

<h4>Data analysis with R ( )</h4>

<ol>
  <li><a href="http://www.datacarpentry.org/R-ecology-lesson/00-before-we-start.html">Overview of R and Rstudio</a> ( mins)</li>
  <li><a href="http://www.datacarpentry.org/R-ecology-lesson/01-intro-to-r.html">Introduction to R</a> ( mins)</li>
  <li><a href="http://www.datacarpentry.org/R-ecology-lesson/02-starting-with-data.html">Working with tabular data in R</a> ( mins)</li>
</ol>

<a href="https://rawgit.com/tavareshugo/2017-09-11-cambridge/gh-pages/materials_recap/day1_recap.html">Recap of R materials from Day 1 ( mins)</a>


<h3>Day 2</h3>


<h4>Data analysis with R</h4>

<ol>
  <li><a href="http://www.datacarpentry.org/R-ecology-lesson/03-dplyr.html">Data manipulation using the R package dplyr</a> ( mins)</li>
  <li><a href="http://www.datacarpentry.org/R-ecology-lesson/04-visualization-ggplot2.html">Data visualisation using the R package ggplot2</a> ( mins)</li>
  <li><a href="http://www.datacarpentry.org/R-ecology-lesson/05-r-and-databases.html">Interacting with databases from R</a> ( mins)</li>
</ol>

Learn more about SQL from the 
<a href="http://www.datacarpentry.org/sql-ecology-lesson/00-sql-introduction/">SQL data lessons</a>.

<p><b> Should you finish earlier than others and want some more challenges please have a go.  
 at this material from the R Software Carpentry course (They could also be done    
 post-course as a revision exercise):</b>   
<a href="http://swcarpentry.github.io/r-novice-gapminder/05-data-structures-part2/index.html">Gapmider R materials</a>

<p><u>Useful reference sheets</u>
<ol>
<li><a href="https://www.rstudio.com/wp-content/uploads/2016/05/base-r.pdf">Base R cheatsheet</a></li>
<li><a href="https://www.rstudio.com/wp-content/uploads/2015/02/data-wrangling-cheatsheet.pdf">Dplyr cheatsheet</a></li>
<li><a href="https://www.rstudio.com/wp-content/uploads/2015/03/ggplot2-cheatsheet.pdf">ggplot2 cheatsheet</a></li>
<li><a href="http://datacamp-community.s3.amazonaws.com/076cc4b0-6e77-4c75-b369-e60d1434817c">Tidyverse cheatsheet</a></li>
	<li><a href="https://github.com/gadenbuie/tidyexplain">Animations of joins, spread & gather</a></li>
</ol>
</p>

{% comment %}
  SYLLABUS

  Show what topics will be covered.

  1. If your workshop is R rather than Python, remove the comment
     around that section and put a comment around the Python section.
  2. Some workshops will delete SQL.
  3. Please make sure the list of topics is synchronized with what you
     intend to teach.
  4. You may need to move the div's with class="col-md-6" around inside
     the div's with class="row" to balance the multi-column layout.

  This is one of the places where people frequently make mistakes, so
  please preview your site before committing, and make sure to run
  'tools/check' as well.

<h2 id="syllabus">Syllabus</h2>

{% if page.carpentry == "swc" %}
  {% include sc/syllabus.html %}
{% elsif page.carpentry == "dc" %}
  {% include dc/syllabus.html %}
{% elsif page.carpentry == "lc" %}
  {% include lc/syllabus.html %}
{% endif %}
{% endcomment %}


<hr/>

{% comment %}
  SETUP

  Delete irrelevant sections from the setup instructions.  Each
  section is inside a 'div' without any classes to make the beginning
  and end easier to find.

  This is the other place where people frequently make mistakes, so
  please preview your site before committing, and make sure to run
  'tools/check' as well.
{% endcomment %}

<h2 id="setup">Setup</h2>

<p>
  To participate in a
  {% if page.carpentry == "swc" %}
  Software Carpentry
  {% elsif page.carpentry == "dc" %}
  Data Carpentry
  {% elsif page.carpentry == "lc" %}
  Library Carpentry
  {% endif %}
  workshop,
  you will need access to the software described below.
  In addition, you will need an up-to-date web browser.
</p>
<p>
  We maintain a list of common issues that occur during installation as a reference for instructors
  that may be useful on the
  <a href = "{{site.swc_github}}/workshop-template/wiki/Configuration-Problems-and-Solutions">Configuration Problems and Solutions wiki page</a>.
</p>


<div id="r"> {% comment %} Start of 'R' section. {% endcomment %}
  <h3>R</h3>

  <p>
    <a href="http://www.r-project.org">R</a> is a programming language
    that is especially powerful for data exploration, visualization, and
    statistical analysis. To interact with R, we use
    <a href="http://www.rstudio.com/">RStudio</a>.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="r-windows">Windows</h4>
      <a href="https://www.youtube.com/watch?v=q0PjTAylwoU">Video Tutorial</a>
      <p>
        Install R by downloading and running
        <a href="http://cran.r-project.org/bin/windows/base/release.htm">this .exe file</a>
        from <a href="http://cran.r-project.org/index.html">CRAN</a>.
        Also, please install the
        <a href="http://www.rstudio.com/ide/download/desktop">RStudio IDE</a>.
        Note that if you have separate user and admin accounts, you should run the 
        installers as administrator (right-click on .exe file and select "Run as 
        administrator" instead of double-clicking). Otherwise problems may occur later, 
        for example when installing R packages.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="r-macosx">macOS</h4>
      <a href="https://www.youtube.com/watch?v=5-ly3kyxwEg">Video Tutorial</a>
      <p>
        Install R by downloading and running
        <a href="http://cran.r-project.org/bin/macosx/R-latest.pkg">this .pkg file</a>
        from <a href="http://cran.r-project.org/index.html">CRAN</a>.
        Also, please install the
        <a href="http://www.rstudio.com/ide/download/desktop">RStudio IDE</a>.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="r-linux">Linux</h4>
      <p>
        You can download the binary files for your distribution
        from <a href="http://cran.r-project.org/index.html">CRAN</a>. Or
        you can use your package manager (e.g. for Debian/Ubuntu
        run <code>sudo apt-get install r-base</code> and for Fedora run
        <code>sudo dnf install R</code>).  Also, please install the
        <a href="http://www.rstudio.com/ide/download/desktop">RStudio IDE</a>.
      </p>
    </div>
  </div>
</div> {% comment %} End of 'R' section. {% endcomment %}


<div id="openrefine"> {% comment %} Start of 'OpenRefine' section. {% endcomment %}
  <h3>OpenRefine</h3>
  <p>
    For this lesson you will need <em>OpenRefine</em> and a
    web browser. <em>Note:</em> this is a Java program that runs on your machine (not in the cloud).
    It runs inside a web browser, but no web connection is needed.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="openrefine-windows">Windows</h4>
      <p>
        Check that you have either the Firefox or the Chrome browser installed and set as your default browser.
        <strong>OpenRefine runs in your default browser.</strong>
        It will not run correctly in Internet Explorer.
      </p>
      <p>Download software from <a href="http://openrefine.org/">http://openrefine.org/</a></p>
      <p>Create a new directory called OpenRefine.</p>
      <p>Unzip the downloaded file into the OpenRefine directory by right-clicking and selecting "Extract ...". </p>
      <p>Go to your newly created OpenRefine directory.</p>
      <p>Launch OpenRefine by clicking <code>google-refine.exe</code> (this will launch a command prompt window, but you can ignore that - just wait for OpenRefine to open in the browser).</p>
      <p>If you are using a different browser, or if OpenRefine does not automatically open for you, point your browser at <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> or <a href="http://localhost:3333">http://localhost:3333</a> to use the program.</p>
    </div>
    <div class="col-md-4">
      <h4 id="openrefine-mac">Mac</h4>
      <p>Check that you have either the Firefox or the Chrome browser installed and set as your default browser. <strong>OpenRefine runs in your default browser.</strong> It may not run correctly in Safari.</p>
      <p>Download software from <a href="http://openrefine.org/">http://openrefine.org/</a>.</p>
      <p>Create a new directory called OpenRefine.</p>
      <p>Unzip the downloaded file into the OpenRefine directory by double-clicking it.</p>
      <p>Go to your newly created OpenRefine directory.</p>
      <p>Launch OpenRefine by dragging the icon into the Applications folder.</p>
      <p>Use <code>Ctrl-click/Open ... </code> to launch it.</p>
      <p>If you are using a different browser, or if OpenRefine does not automatically open for you, point your browser at <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> or <a href="http://localhost:3333">http://localhost:3333</a> to use the program.</p>
    </div>
    <div class="col-md-4">
      <h4 id="openrefine-linux">Linux</h4>
      <p>Check that you have either the Firefox or the Chrome browser installed and set as your default browser. <strong>OpenRefine runs in your default browser.</strong></p>
      <p>Download software from <a href="http://openrefine.org/">http://openrefine.org/</a>.</p>
      <p>Make a directory called OpenRefine.</p>
      <p>Unzip the downloaded file into the OpenRefine directory.</p>
      <p>Go to your newly created OpenRefine directory.</p>
      <p>Launch OpenRefine by entering <code>./refine</code> into the terminal within the OpenRefine directory.</p>
      <p>If you are using a different browser, or if OpenRefine does not automatically open for you, point your browser at <a href="http://127.0.0.1:3333/">http://127.0.0.1:3333/</a> or <a href="http://localhost:3333">http://localhost:3333</a> to use the program.</p>
    </div>
  </div>
</div> {% comment %} End of 'OpenRefine' section. {% endcomment %}

{% comment %}
<div id="vm">
  <h3>Virtual Machine</h3>

  <p>
    Some instructors prefer to have learners use a virtual machine (VM)
    rather than install software on their own computers.  If your
    instructors have chosen to do this, please:
  </p>
  <ol>
    <li>
      Install <a href="https://www.virtualbox.org/">VirtualBox</a>.
    </li>
    <li>
      Download our <a href="{{site.swc_vm}}">VM image</a>.
      <strong>Warning:</strong> this file is 1.7 GByte, so please
      download it <em>before</em> coming to your workshop.
    </li>
    <li>
      Load the VM into VirtualBox by selecting "Import Appliance" and
      loading the <code>.ova</code> file.
    </li>
  </ol>
</div>
{% endcomment %}


<div id="sql"> {% comment %} Start of 'SQLite' section. {% endcomment %}
  <h3>SQLite</h3>

  <p>
    SQL is a specialized programming language used with databases.  We
    use a simple database manager called
    <a href="http://www.sqlite.org/">SQLite</a> in our lessons.
  </p>

  <div class="row">
    <div class="col-md-4">
      <h4 id="sql-windows">Windows</h4>
      <p>
        The <a href="{{site.swc_installer}}">
          {% if page.carpentry == "swc" %}
          Software Carpentry
          {% elsif page.carpentry == "dc" %}
          Data Carpentry
          {% elsif page.carpentry == "lc" %}
          Library Carpentry
          {% endif %}
          Windows Installer
	</a>
        installs SQLite for Windows.
        If you used the installer to configure nano, you don't need to run it again.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="sql-macosx">macOS</h4>
      <p>
        SQLite comes pre-installed on macOS.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="sql-linux">Linux</h4>
      <p>
        SQLite comes pre-installed on Linux.
      </p>
    </div>
  </div>

  <p><strong>If you installed Anaconda, it also has a copy of SQLite
    <a href="https://github.com/ContinuumIO/anaconda-issues/issues/307">without support to <code>readline</code></a>.
    Instructors will provide a workaround for it if needed.</strong></p>
</div> {% comment %} End of 'SQLite' section. {% endcomment %}

