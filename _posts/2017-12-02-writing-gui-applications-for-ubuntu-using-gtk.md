---
layout: post
title:  "Writing GUI Applications with Gtk+"
author: "Shalitha Suranga"
---

[GTK+](https://en.wikipedia.org/wiki/GTK%2B) was originally developed for GIMP photo editing software of GENOME project. Where as nowadays it is very popular cross platform GUI toolkit. The core of GTK+ is written with C Programming language.

Here I am going to show you how you can start working with GTK on Linux.

### Installation 

```bash
 $ sudo apt-get install libgtk-3-dev
```

This will install the GTK+ version 3 toolkit on your Linux PC.

### Writing Code

GTK+ based applications can be written using C,C++,Python or Java. Let's start with simple program with c only with Text Label on a window.

Filename : `helloworld.c`

```C
#include <gtk/gtk.h>

int main (int argc, char *argv[])
{
    GtkWidget *window;
    GtkWidget *label;

    gtk_init(&argc, &argv);

    /* Create the main, top level window */
    window = gtk_window_new(GTK_WINDOW_TOPLEVEL);

    /* Give it the title */
    gtk_window_set_title(GTK_WINDOW(window), "Hello, world!");

    /* Center the window */
    gtk_window_set_position(GTK_WINDOW(window), GTK_WIN_POS_CENTER);

    /* Set the window's default size */
    gtk_window_set_default_size(GTK_WINDOW(window), 200, 100);

    /*
    ** Map the destroy signal of the window to gtk_main_quit;
    ** When the window is about to be destroyed, we get a notification and
    ** stop the main GTK+ loop by returning 0
    */
    g_signal_connect(window, "destroy", G_CALLBACK(gtk_main_quit), NULL);

    /*
    ** Assign the variable "label" to a new GTK label,
    ** with the text "Hello, world!"
    */
    label = gtk_label_new("Hello, GTK+!");

    /* Plot the label onto the main window */
    gtk_container_add(GTK_CONTAINER(window), label);

    /* Make sure that everything, window and label, are visible */
    gtk_widget_show_all(window);

    /*
    ** Start the main loop, and do nothing (block) until
    ** the application is closed
    */
    gtk_main();

    return 0;

}
```

### How to Compile

```bash
$ gcc helloworld.c -o helloworld `pkg-config --cflags --libs gtk+-3.0`
```

### How to Execute





