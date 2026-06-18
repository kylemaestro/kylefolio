```
██╗  ██╗██╗   ██╗██╗     ███████╗███████╗ ██████╗ ██╗     ██╗ ██████╗ 
██║ ██╔╝╚██╗ ██╔╝██║     ██╔════╝██╔════╝██╔═══██╗██║     ██║██╔═══██╗
█████╔╝  ╚████╔╝ ██║     █████╗  █████╗  ██║   ██║██║     ██║██║   ██║
██╔═██╗   ╚██╔╝  ██║     ██╔══╝  ██╔══╝  ██║   ██║██║     ██║██║   ██║
██║  ██╗   ██║   ███████╗███████╗██║     ╚██████╔╝███████╗██║╚██████╔╝
╚═╝  ╚═╝   ╚═╝   ╚══════╝╚══════╝╚═╝      ╚═════╝ ╚══════╝╚═╝ ╚═════╝                                                         

             *** installation and dev guide ***
       ===============================================


                      ~ WELCOME, TRAVELER! ~

    Go back in time with our all-in-one retro portfolio package!

                  Live @ http://kylemeister.dev


  +------------------------------------------------------------+
  |  ARCHITECTURE                                              |
  +------------------------------------------------------------+

    src/
      index.html    the whole site. markup + inline styles +
                    DC components, all in one file.
      support.js    the "dc-runtime" -- a little React-based
                    component runtime. GENERATED. hands off.
      CNAME         custom domain for GitHub Pages.
      uploads/      images (profile pic, whatever else).

    .github/workflows/deploy.yml
                    ships src/ to GitHub Pages on push to main.

  index.html is carved into commented chunks -- BANNER, MARQUEE, NAV,
  ABOUT, PROJECTS, SOCIALS, GUESTBOOK, THEME SELECTOR, FOOTER, and the
  TERMINAL OVERLAY. grep for `===== SECTION =====` to teleport around.

     //!\\ support.js is generated from a separate dc-runtime
     (TypeScript) project. Edit it by hand and your changes
     evaporate on the next rebuild. You have been warned.


  +------------------------------------------------------------+
  |  RUNNING IT ON YOUR OWN MACHINE                            |
  +------------------------------------------------------------+

  It's static. Serve src/ with whatever you've got lying around:

      cd src
      python -m http.server 8000     # http://localhost:8000

  Opening index.html straight in a browser works too, but a local
  server keeps the fonts and paths happy.


  +------------------------------------------------------------+
  |  RUNNING IT ON A DIFFERENT MACHINE                         |
  +------------------------------------------------------------+

  Push straight to prod (main). deploy.yml grabs src/
  and publishes it to GitHub Pages. To wire this up
  on a fresh fork:

    1. Settings -> Pages -> Build and deployment -> Source:
       "GitHub Actions".
    2. Push to main.
    3. Check Pages settings for live URL.


  +------------------------------------------------------------+
  |  USING YOUR OWN DOMAIN                                     |
  +------------------------------------------------------------+

    1. Drop your domain in src/CNAME, one line (e.g. yourcooldomain.dev).
       It rides along with the site.

    2. At your DNS provider, point at GitHub Pages:

         apex (example.com):
           A  ->  185.199.108.153
           A  ->  185.199.109.153
           A  ->  185.199.110.153
           A  ->  185.199.111.153

         subdomain (www.example.com):
           CNAME  ->  <your-username>.github.io

    3. Settings -> Pages: punch in the domain, tick "Enforce HTTPS"
       once the cert shows up.

  DNS takes its sweet time. Grab a coffee, come back, you're live.


       ===============================================
            powered by coffee and Claude tokens
            best viewed in Netscape Navigator!
       ===============================================
```
