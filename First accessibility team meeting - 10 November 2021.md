present: gwynn, Heather, Jonathan Godfrey, Di Cook, Zane, Mine, Florencia, Liz Hare

Agenda:
 
    
1. Goals - accessibility and what it means  --     "what is accessibility?' in the R community
    a formal statement about accessibility in terms of conferences and websites. 
    differing views about accessibility - US vs UK vs Aus vs NZ, some countries do not acknowledge their disabled Getting the language right can really make conferences and other events more welcoming.
    CRAN - not so much, finding download for R in windows is not user-friendly, work on improving the experience --The issue with downloading R from CRAN for Windows: https://github.com/RConsortium/r-repositories-wg/issues/5 - it is hard to find the link, so unfriendly.
 - so more about improving experience than accessibility
    building and conferences are accessible
    smaller venues, online platforms not so very accesssible, web standards have changed 
    Websites have universal accessibility guidelines but ** not user friendly ** 
Calendar links are hard to read, links in email is easier 
GitHub is less screenreader accessible compared to 4 years ago according to Jonathan's needs - not everything in hands of R communityGitHub pull requests? a way to push the issue forwards 
 voice over reader for readability (Mac user) If you're on Windows and want an open source screen reader to try out, here's a link to NVDA: https://www.nvaccess.org/download/

1a. Adding information - blog post on accesibility issues
    conferences - the link below should be easier to find - also want feedback  https://github.com/forwards/event_best_practices/blob/master/DRAFTEventBestPracticesDisability.md
Forwards links are in need of work, delete (or fix) deadlinks

3. Check accessibility of the new R Journal style: https://journal.r-project.org/dev/: 
        add dark mode toggle + font size increase (?)
        alt-text on figures: authors need to provide this
        convert past pdf to html (huge job!) see https://tug.org/tex4ht/
RJournal - articles now in html, dark mode available for only a few R references, can be updated using html,     Jonathan would like to work on converting R journal from pdf to html - mktex has tex4ht that can convert to html, how good will the html look with this conversion.

Package documentation - vignettes are in sweave that are not accessible, must be updated into html - conversion from Rmw to Rmd files - Rd files are tex file - Rmd is much more accessible than docx and other files
help pages need work .

    
    2. Perhaps Slackathon talk sometime in the next year?
dark mode HTML/ CSS code block for toggle between white/ dark background and font, as well as increase font size is also very helpful

my link to a dark mode toggle button {Zane}  : ( this is an example code to show how to add dark mode toggle to HTML )
 https://github.com/PythonCoderUnicorn/DarkMode_toggle/blob/main/darkmode.html

Markdown file is preferrable for accessibility 

Easy wins - Dark mode toggle button - for R - will need to discuss with RCore https://github.com/PythonCoderUnicorn/DarkMode_toggle/blob/main/darkmode.html
 - who implemented table at top of help pages between R 3 and R 4 might be able to help?
 - altering the process that converts the Rd files to HTML will have a large impact with not so much effort on the part of the package developers
- help pages, webpages, vignettes,
- JSS - also could use html versions
Issue on pkgdown on dark mode: https://github.com/r-lib/pkgdown/issues/1696

Zane - every two weeks -  help: "Package documentation - vignettes are in sweave that are not accessible, must be updated into html"  << need to look into more of this 

Di and Jonathan work on RJournal together

Jonathan and reach out to Achim - influencing R GUI for dark mode
