---
title: Building A Decentralized Portfolio Website
date: 2021-09-14T11:52:24.781Z
summary: With the introduction of Web 3.0 there are endless possibilities to
  build new applications and monetize them. This blog walks you through the
  process of building and maintaining a custom, cross platform, decentralized
  website which can be easily maintained.
draft: false
featured: false
categories:
  - Development
  - Tech
image:
  filename: featured.jpg
  focal_point: Smart
  preview_only: false
---
<!--StartFragment-->

\# Creating a Decentralized Portfolio Website

\## What is a Portfolio Website ??

 A portfolio website is an essential tool to getting more business and building your professional brand. In today’s digital world, a portfolio is arguably more important than a resume, no matter what industry you work in. Whether you are a freelance journalist, a recent college grad looking for a job, or even an accountant, when people Google your name, your portfolio will provide the most powerful and comprehensive perspective on you.

\## Awesome where do I start ?

\### Lets choose a tech stack

It can be just pure HTML , CSS or can we can use JS frameworks like React or Angular or Vue Ember or Meteor or Mithril the list goes on and on for Javascript \*\*FacePalm\*\*  But here we are going to use Flutter !!!

\### What is Flutter ??

Flutter is Google’s UI toolkit for building beautiful, natively compiled applications for mobile, web, and desktop from a single codebase.

Say what?? a single framework for web , mobile , desktop ??  Even on a Raspberry Pi : >

The basics of Flutter can be learned in the link below

\[Flutter Basics](https://github.com/HariPranav/Flutter)

\[Flutter Advanced](https://github.com/HariPranav/flutter_learning_path)

\# Without installing Flutter on Local Machine

!\[Basic UI](https://raw.githubusercontent.com/HariPranav/BENIMAGES/master/Screen1.png)

Go to the link below and paste the code below

\[DartPad](https://github.com/HariPranav/Flutter)

    import 'package:flutter/material.dart';

    void main()

    {

        runApp(MyApp());

    }

    class MyApp extends StatefulWidget {

    @override

    _MyAppState createState() => _MyAppState();

    }

    class _MyAppState extends State<MyApp> {

     @override

    Widget build(BuildContext context) {

    return MaterialApp(

      debugShowCheckedModeBanner: false,

      home: Scaffold(

        body: Container(

          decoration: BoxDecoration(

            image: DecorationImage(

              image: NetworkImage("https://images-wixmp-ed30a86b8c4ca887773594c2.wixmp.com/i/0052d15d-4c44-4d0f-aade-45074bff0633/d9erbf9-27735655-772d-437a-ae35-ef67e1ea9d10.jpg"),

              fit: BoxFit.fill

              ,

            ),

          ),

          child: ListView(children: [

            Center(

              child: Container(

                margin: EdgeInsets.all(40),

                height: 150,

                width: 150,

                decoration: BoxDecoration(

                  shape: BoxShape.circle,

                  image: DecorationImage(

                      image: NetworkImage('https://scontent.fblr2-1.fna.fbcdn.net/v/t1.0-1/c0.120.320.320a/p320x320/45144634_1855611297884897_6210030828886425600_n.jpg?_nc_cat=105&_nc_sid=7206a8&_nc_oc=AQmllP_29URGPDyNhajv3rw2YzkqMeeukAQiwgSKm4XJRBhNI533aqwYd13gJN8DdS0&_nc_ht=scontent.fblr2-1.fna&oh=2919360f49c924ee76c6c2f60fc56325&oe=5F1416AE'),

                      fit: BoxFit.contain),

                ),

              ),

            ),

            Center(

              child: Container(

                decoration: BoxDecoration(

                  borderRadius: BorderRadius.all(Radius.circular(20)),

                  gradient: LinearGradient(

                    begin: Alignment.bottomLeft,

                    end: Alignment.bottomRight,

                    colors: \[Colors.green[50], Colors.red\[300]],

                  ),

                ),

                margin: EdgeInsets.all(10),

                padding: EdgeInsets.all(5),

                child: Text(

                  " Flutter | Blockchain | Forensics",

                  style: TextStyle(

                    color: Colors.black,

                    fontSize: 20,

                  ),

                ),

              ),

            ),

            Center(

              child: Container(

                decoration: BoxDecoration(

                  borderRadius: BorderRadius.all(Radius.circular(20)),

                  gradient: LinearGradient(

                    begin: Alignment.bottomRight,

                    end: Alignment.bottomLeft,

                    colors: \[Colors.green[50], Colors.red\[300]],

                  ),

                ),

                margin: EdgeInsets.all(10),

                padding: EdgeInsets.all(5),

                child: Row(mainAxisSize: MainAxisSize.min, children: <Widget>[

                  InkWell(

                      child: Image.network(

                        "https://cdn.icon-icons.com/icons2/936/PNG/128/github-logo_icon-icons.com_73546.png",

                        height: 40,

                        width: 40,

                      ),

    //                       onTap: () => launch('https://github.com/HariPranav')

                  ),

                  SizedBox(

                    width: 8,

                  ),

                  InkWell(

                    child: Image.network(

                      "https://cdn.icon-icons.com/icons2/31/PNG/128/sociallinkedin_member_2751.png",

                      height: 40,

                      width: 40,

                    ),

    //                     onTap: () => launch(

    //                         'https://in.linkedin.com/in/hari-pranav-77b067162'),

                  ),

                  SizedBox(

                    width: 8,

                  ),

                  InkWell(

                    child: Image.network(

                      "https://cdn.icon-icons.com/icons2/555/PNG/128/facebook_icon-icons.com_53612.png",

                      height: 40,

                      width: 40,

                    ),

        //                     onTap: () =>

        //                         launch('https://www.facebook.com/hari.pranav.1'),

                  ),

                  SizedBox(

                    width: 8,

                  ),

                  InkWell(

                    child: Image.network(

                      "https://cdn.icon-icons.com/icons2/122/PNG/128/twitter_socialnetwork_20007.png",

                      height: 40,

                      width: 40,

                    ),

        //                     onTap: () => launch('https://twitter.com/aharipranav'),

                  ),

                  SizedBox(

                    width: 8,

                  ),

                  InkWell(

                    child: Image.network(

                      "https://cdn.icon-icons.com/icons2/195/PNG/128/YouTube_23392.png",

                      height: 40,

                      width: 40,

                    ),

        //                     onTap: () => launch(

        //                         'https://www.youtube.com/channel/UCWYIT8-ScPTy-fWSa3ff6_A?view_as=subscriber'),

                  ),

                ]),

              ),

            ),

          ]),

        ),

        ),

        );

     }

    }

Here we are using the online tool called dartpad to render the UI into the browser , you might have observed that the on Tap handlers in the code are commented this is because we need to install a package which is currently not supported, so when we click a social media icon it doesn't link anywhere. Hence we need to install flutter and dart in our local environment to add hyperlinking functionality!!

\# With Flutter on Local Machine

Installing Flutter  : \[Documentation](https://flutter.dev/docs/get-started/install)

\### Step 1 :

After installing flutter we need to build the application on the web so change the branch to web

   $flutter channel master

   $flutter upgrade

   $flutter config --enable-web

\### Step 2 :

Run

   $flutter devices

Here we should see chrome as the devices available , PS : if it doesnt show up check if you have the latest version of chrome

\### Step 3  :

Run:

  $flutter create <your-name>

\### Step 4  :

Lets get coding !!!

Open the pubspec.yaml and go to the commented section under dependencies

        dependencies:

        flutter:

            sdk: flutter

            // paste this code below

        url_launcher: ^5.4.10

Go to the terminal and type

    $pub get

This installs the dependencies

Next Open the main.dart under the lib directory in your project

Then paste the code below

    // importing the libraries

    import 'package:flutter/material.dart';

    import 'package:url_launcher/url_launcher.dart';

    // creating a stateful widget

    // type stf and it auto creates one (Works in vs code and android studion with )

    void main()

    {

        runApp(MyApp());

    }

    class MyApp extends StatefulWidget {

    @override

    _MyAppState createState() => _MyAppState();

    }

    class _MyAppState extends State<MyApp> {

    @override

    Widget build(BuildContext context) {

        return MaterialApp(

            // we check the debug banner to be false

        debugShowCheckedModeBanner: false,

        // the scaffold basically provides predefined //material components to be used in UI

        home: Scaffold(

            // we use a container to display the Image

            body: Container(

            decoration: BoxDecoration(

                image: DecorationImage(

                    // create a folder called assets in the parent directory of your project and put your profile photo to be displayed

                image: AssetImage("assets/ss2.jpg"),

                fit: BoxFit.cover,

                ),

            ),

            child: ListView(children: [

                Center(

                child: Container(

                    margin: EdgeInsets.all(40),

                    height: 150,

                    width: 150,

                    decoration: BoxDecoration(

                    shape: BoxShape.circle,

                    image: DecorationImage(

                        image: AssetImage('assets/HP.png'), fit: BoxFit.contain),

                    ),

                ),

                ),

                Center(

                child: Container(

                    // we use the famous Linear Gradient

                    decoration: BoxDecoration(

                    borderRadius: BorderRadius.all(Radius.circular(20)),

                    gradient: LinearGradient(

                        begin: Alignment.bottomLeft,

                        end: Alignment.bottomRight,

                        colors: \[Colors.green[50], Colors.red\[300]],

                    ),

                    ),

                    margin: EdgeInsets.all(10),

                    padding: EdgeInsets.all(5),

                    child: Text(

                    " Flutter | Blockchain | Forensics",

                    style: TextStyle(

                        color: Colors.black,

                        fontSize: 20,

                    ),

                    ),

                ),

                ),

                Center(

                child: Container(

                    decoration: BoxDecoration(

                    borderRadius: BorderRadius.all(Radius.circular(20)),

                    gradient: LinearGradient(

                        begin: Alignment.bottomRight,

                        end: Alignment.bottomLeft,

                        colors: \[Colors.green[50], Colors.red\[300]],

                    ),

                    ),

                    margin: EdgeInsets.all(10),

                    padding: EdgeInsets.all(5),

                    child: Row(mainAxisSize: MainAxisSize.min, children: <Widget>[

                        // here we add the links to our varoius social media websites

                    InkWell(

                        child: Image.asset(

                            "assets/github.png",

                            height: 40,

                            width: 40,

                        ),

                        onTap: () => launch('https://github.com/HariPranav')),

                    SizedBox(

                        width: 8,

                    ),

                    InkWell(

                        child: Image.asset(

                        "assets/linkedin-square-color.png",

                        height: 40,

                        width: 40,

                        ),

                        onTap: () => launch(

                            'https://in.linkedin.com/in/hari-pranav-77b067162'),

                    ),

                    SizedBox(

                        width: 8,

                    ),

                    InkWell(

                        child: Image.asset(

                        "assets/facebook-round-color.png",

                        height: 40,

                        width: 40,

                        ),

                        onTap: () => launch(

                            'https://www.facebook.com/hari.pranav.1'),

                    ),

                    SizedBox(

                        width: 8,

                    ),

                    InkWell(

                        child: Image.asset(

                        "assets/twitter-color.png",

                        height: 40,

                        width: 40,

                        ),

                        onTap: () => launch('https://twitter.com/aharipranav'),

                    ),

                    SizedBox(

                        width: 8,

                    ),

                    InkWell(

                        child: Image.asset(

                        "assets/youtube-color.png",

                        height: 40,

                        width: 40,

                        ),

                        onTap: () => launch(

                            'https://www.youtube.com/channel/UCWYIT8-ScPTy-fWSa3ff6_A?view_as=subscriber'),

                    ),

                    ]),

                ),

                ),

            ]),

            ),

        ),

        );

            }

        }

go to the terminal and type

    $flutter run -d chrome

Voila your Single Page Website is Ready on the web!!! This can also be run as a standalone app on your android phone or IOS device !!

To do so change the branch to stable by using the command

    $flutter channel stable

Anyways Lets get to hosting our Website on the web

\# Adding Project to Github

Go to github and create a new repository

Add the name

And a short description

Leave the intitalize a Readme as unticked and say create repository

Now open the command Line and

Run

    $git init

    $git add .

    $git commit -m "First commit"

    $git remote add "URL of repo"

    $git push -u origin master

Now go to settings and enable the githubpages option

Then Run the following Commands in your flutter project

    $flutter pub global activate peanut

    $flutter pub global run  peanut

    $git push origin --set-upstream gh-pages

Finally you are done !!!!

The page is now hosted on github as the centralised version !!

Fell free to share this url with your friends family and employer's

Hoorah Lets Decentralize It

\# Decentralization

\## What is IPFS ??

A peer-to-peer hypermedia protocol

designed to make the web faster, safer, and more open.

 \[IPFS](https://ipfs.io/)

\## What is fleek ??

On IPFS , Fleek provides a beautiful way to integrate with Git so that whenever we make changes to our branches it can be directly

updated on Fleek!!!!

\### Hosting on Fleek 

Click on the link below to know more here we can directly login with our git account and host our website

\[Fleek](https://github.com/login?client_id=1cfc1c05c0a7ac516723&return_to=%2Flogin%2Foauth%2Fauthorize%3Fclient_id%3D1cfc1c05c0a7ac516723%26redirect_uri%3Dhttps%253A%252F%252Fauth.fleek.co%252Fgithub%252Fcallback%253Fstate%253D%252Finteraction%252FZHuHDYZi80oBowaz9y03R%252Fgithub%252Fcallback%26response_type%3Dcode%26scope%3Duser%253Aemail)

Different CMS to host sites on fleek Link Below

\[Fleek Blog posts](https://blog.fleek.co/)

\# Find Me !!

I have added more pages on for my porfolio such as an animated bottom navigation bar with custom images , a blog section and a short demo of my hackathon projects which will be added soon 

Find me on the web below !!

\[My Portfolio](https://haripranav.github.io/portfolio/#/)

\[My Decentralized Portfolio](https://hp.on.fleek.co/#/)

<!--EndFragment-->