JAZBEDO — personal creator site
================================

This repo is the whole website. It is plain HTML, CSS, and JavaScript.
No install step, no build tool, no account, and no payment is required
to edit it. You can open index.html on your own computer before you
publish.


1. Design
----------

One scrolling page, like a winter atelier index rather than a card grid.

- Charcoal page (#141311), ivory text (#f4f0e6), muted gold lines
  (#d4bc82 and #a68546), and a restrained teal (#8ecfc6).
- Headings use Palatino or Georgia (already on Windows and Mac).
  Body text uses Segoe UI, Candara, or Calibri, then a generic sans.
- Navigation is a row of text links: Intro, Social, Cosplay, Voice.
  On a narrow screen they wrap under the name. They are real links.
- The portrait and the cosplay slots are framed plates (gold outer
  line, teal inner line), not rounded cards.
- A short opening curtain can appear for about three seconds. It is
  skippable. The page underneath is already there. If JavaScript is
  off, motion is reduced, or the browser is too old, the curtain
  never appears.


2. How the old-browser version stays intentional
-------------------------------------------------

The first version of the layout is just stacked blocks, normal colors,
and normal links. Wider screens get two columns only inside
"@media (min-width)" rules. If a browser ignores those rules, you still
get the readable stacked page in the same colors, same order, same words.

JavaScript only does two extra things: the opening curtain, and a larger
view when a cosplay picture is clicked. Without JavaScript, that click
opens the image file itself. Audio uses the browser's own player and
never starts by itself. If a browser has no player, the "Open or
download" link under each sample still works.

What this cannot promise: Internet Explorer, and very old phones, may
ignore the media rules or the SVG drawings. The words and links remain.
See section 9.


3. Files
--------

index.html          The page. Edit the words here.
css/site.css        Colors, type, and layout.
js/site.js          Opening curtain and larger pictures. Optional.
favicon.svg         Small tab icon.
images/hero.svg     Stand-in portrait. Replace with your artwork.
images/gallery/     Stand-in cosplay plates. Replace with photos.
README.txt          This guide.
.nojekyll           Lets GitHub Pages serve the folder as-is.


4. Where to put my files
--------------------------

Portrait
  Save your drawing as images/hero.jpg (or .png, or .webp).
  In index.html, change the portrait line from images/hero.svg to
  images/hero.jpg and rewrite the alt text so it describes your picture
  (your face, the fennec persona, the costume, the setting).

  Optional background behind the introduction block:
  save a compressed JPEG as images/hero-bg.jpg, then in css/site.css
  find the comment inside ".hero" and uncomment the background-image
  lines. If that file fails to load, the charcoal plate color remains.

Cosplay
  For each look, export two JPEGs:
    images/gallery/look-05-thumb.jpg   about 800px on the long edge
    images/gallery/look-05.jpg         about 1600px on the long edge
  Copy a <figure> block in index.html (there is a comment that shows
  the pattern). Point src at the thumb and href at the large file.
  Write alt text that describes that photo. The path line under the
  caption is only a reminder; you can delete the <span class="path">
  once you no longer need it.

Compressing images for free
  Phone photos are often 3–8 MB. That is too heavy for this site.
  1. Shrink the long edge to about 1600px (full) or 800px (thumbnail).
     Windows Paint, Paint.NET, or GIMP can do this. GIMP is free.
     On a phone, the built-in editor's export or a resize app is enough.
  2. Open https://squoosh.app in a current browser (it runs on your
     computer; the picture is not uploaded to a host).
  3. Choose MozJPEG. Start near quality 70. Move it until the picture
     still looks clean.
  4. Aim for about 100–250 KB for the main portrait, under about 180 KB
     for a gallery photo, and under about 60 KB for a thumbnail.
  5. Do not upload camera originals. Avoid PNG for photos; PNG is for
     flat drawings and the icon.

A typical visit, before my photos, is well under 150 KB. After you
add a portrait and a few thumbs it should stay near 150–400 KB if you
follow the sizes above. Large files are not loaded until a visitor
opens that picture or presses play.


5. What to edit
---------------

All of this is in index.html unless noted. Search for "EDIT:".

Words
  The heading "Jazbedo", the italic tagline, and the two introduction
  paragraphs.

Interests
  The list Cosplay, Gaming, Voice acting, Virtual creation.

Social links
  Every address currently contains YOUR_ in capital letters. Replace
  the whole href and the hint text. Examples of the shape, not real
  accounts:
    https://www.tiktok.com/@YOUR_TIKTOK_HANDLE
    https://www.youtube.com/@YOUR_YOUTUBE_HANDLE
    https://www.twitch.tv/YOUR_TWITCH_HANDLE
    https://x.com/YOUR_X_HANDLE
    https://www.instagram.com/YOUR_INSTAGRAM_HANDLE
    https://www.facebook.com/YOUR_FACEBOOK_PAGE
    https://open.spotify.com/user/YOUR_SPOTIFY_ID
    https://example.com/YOUR_OTHER_PROFILE
  Spotify is only a link, not an embedded player.
  To add a platform, copy one <li>...</li> block. The text label is
  required. The little icon is optional.

Colors
  css/site.css, the list at the top. Search for the hex code and
  replace every use of it so the page stays consistent. The same
  colors are used in the simple layout and the wider layout.

Navigation
  The <nav> links point at #content, #social, #cosplay, and #voice.
  To rename a section, change the visible words and, if you want,
  the id on that <section>. Keep the href and the id the same.

Year and contact
  The footer has "© 2026 Jazbedo." and you@example.com.
  Change the year by hand when the year changes. Change the mailto
  address in both places (the href and the visible text).

Opening curtain
  It shows once per browser tab, then stays away until the tab is
  closed. To show it on every visit, delete the sessionStorage lines
  in js/site.js (the key is jazbedo-opened). To remove the curtain
  entirely, delete the <div id="opening"> block. The rest of the page
  does not need it.

Pictures and audio
  See section 4.


6. Publish for free
--------------------

Recommended: Cloudflare Pages, on the free plan.
Checked against Cloudflare's docs (Pages limits, updated Sep 2026;
direct upload, updated Apr 2026):

- A free subdomain such as jazbedo.pages.dev. You pick the project name.
- HTTPS is on by default.
- Unlimited bandwidth for static files (HTML, CSS, JavaScript, images,
  audio). This site does not use Pages Functions, so the Workers
  request cap does not apply.
- Up to 100 projects, 20,000 files on a Git deploy, 25 MB per file.
- Direct upload from the dashboard is capped more tightly (about 1,000
  files). This site is a handful of files, so that is plenty.
- 500 Git builds per month if you later connect a repository. Direct
  upload does not need a build.
- A paid plan is not required. If a signup screen insists on a card,
  skip it and use GitHub Pages below instead.

Steps:

1. Create a free account at https://dash.cloudflare.com/sign-up
2. Open Workers & Pages, then Create, then Pages.
3. Choose the direct upload option ("Upload assets" / drag and drop),
   not a framework template.
4. Name the project jazbedo if that name is free. The public address
   will be https://jazbedo.pages.dev
5. Upload this folder, or a zip of this folder. index.html must sit at
   the top of what you upload, not inside an extra folder.
   The dashboard accepts a zip. The Wrangler command-line tool wants
   the folder itself, not a zip.
6. Deploy, then open the pages.dev address.
7. When you change a word or a photo, upload the folder again the same
   way. You do not need a developer for that.

GitHub Pages, if you would rather not use Cloudflare:

1. Make a free account at https://github.com
2. Create a public repository named exactly yourname.github.io
   (use your GitHub username).
3. Upload every file in this folder to that repository. Include the
   .nojekyll file so GitHub does not run a builder over the site.
4. Settings, then Pages, then branch "main" and folder "/ (root)",
   then Save.
5. After a minute or two the site is at https://yourname.github.io
6. GitHub Pages is also free HTTPS. The soft limit is about 1 GB of
   files and a suggested 100 GB of traffic a month, which is more than
   enough for a personal atelier. There is no card.

Do not buy a domain unless you want one later. Both options work on
the free subdomain.


7. How to test
--------------

On your computer
  Double-click index.html, or drag it into a current browser.
  Check the introduction, every social link (they will 404 until you
  replace YOUR_... with real addresses), a cosplay picture, and a
  voice player. Confirm the player does not start by itself.

Narrow phone
  In the browser's tools, use a width around 390px, or just open the
  pages.dev address on your phone. Nothing should stick out sideways.
  The section links should be easy to tap.

JavaScript off
  In Firefox: Settings, Privacy, Custom, uncheck JavaScript.
  Or in Chrome DevTools, Command menu, "Disable JavaScript".
  Reload. You should see the full page immediately, with no curtain.
  Social links still go out. A cosplay picture opens as a plain image.
  Audio still has a player or, if the player is missing, a download link.

Reduced motion
  In the operating system, turn on "reduce motion" / "show animations"
  off. Reload. The curtain should not appear, and the seal should not
  spin.

An older computer
  A Windows 7 virtual machine with the last Chrome or Firefox that
  still installs there is a fair test. Expect the same colors and the
  same sections. If the browser is too old for modern HTTPS, the
  problem is the connection, not the page. See below.


8. Limits, stated honestly
--------------------------

- Windows Vista, and Windows 7 that never received updates, often cannot
  open today's HTTPS sites. Cloudflare and GitHub both require modern
  TLS. There is no switch in this project that weakens that, and you
  should not bypass certificate warnings. On those machines, use a
  browser build that still supports TLS 1.2, or open index.html from
  a USB stick as a local file.
- This site does not claim to work in Internet Explorer. IE 11 may show
  a plain stacked page. Older IE may not.
- SVG drawings (the stand-in plates and the ear mark) need a browser
  that understands SVG. The words do not.
- TikTok, Instagram, X, YouTube, Twitch, Facebook, and Spotify decide
  their own browser support. A correct link from this page can still
  fail on an old phone because their site refused the browser.
- The opening animation uses position:fixed and a little JavaScript.
  If either is missing, the curtain is skipped on purpose.
- Audio needs MP3 support or the download link. Players are the
  browser's own controls, so they look slightly different everywhere.
- No visitor counter, no ads, no third-party fonts. The page will not
  show you statistics.
- The geometric ears and circle are an original mark for Jazbedo.
  They are not official Genshin Impact art, and this site is not an
  official Genshin Impact site.
