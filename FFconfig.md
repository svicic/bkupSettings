# Add-ons
* https://github.com/ivanruvalcaba/BehindTheOverlayRevival
* https://github.com/marklieberman/foxygestures
* https://gitlab.com/kroppy/TreeTabs (my dark theme)

# userChrome.css
after Shadowfox install append here:  
Help > Troubleshooting Information > Profile Folder (Open Folder) > chrome > userChrome.css   
 
```
/* removes tabs at the top */
#titlebar {margin-bottom: 0px !important;}
#tabbrowser-tabs {visibility: collapse !important;}




/* Modify to change window drag space width */
/*
Use Fx65_tabs_on_bottom_menubar_on_top_patch if you
have menubar permanently enabled and want it on top
 */

 :root{ --uc-titlebar-padding: 0px; --uc-window-control-width: 138px }
 :root[sizemode="maximized"][tabsintitlebar]{ --uc-titlebar-padding: 8px }
 :root[tabsintitlebar="true"] #nav-bar{ --window-drag-space-width: 15px; }
 
 
 .titlebar-buttonbox-container{
   position: fixed;
   top: var(--uc-titlebar-padding,0px);
   right:0;
   height: 40px;
 }
 
 :root[uidensity="compact"] .titlebar-buttonbox-container{ height: 32px }
 
 #toolbar-menubar[inactive] > .titlebar-buttonbox-container{ opacity: 0 }
 
 #navigator-toolbox{ padding-top: var(--uc-titlebar-padding,0px) !important; }
 
 
 .titlebar-buttonbox-container > .titlebar-buttonbox{ height: 100%; }
 
 #titlebar{
  -moz-box-ordinal-group: 2;
   -moz-appearance: none !important;
 }
 
 :root[tabsintitlebar="true"] #nav-bar{
  padding-right: calc(var(--uc-window-control-width) + var(--window-drag-space-width,0px));
  padding-left: var(--window-drag-space-width,0px)
}
 
 .titlebar-placeholder,
 #TabsToolbar .titlebar-spacer{ display: none; }
 /* Also hide the toolbox bottom border which isn't at bottom with this setup */
 #navigator-toolbox::after{ display: none !important; }


/*
BOOKMARK BAR
*/
/* Hides bookmark text for all bookmarks displayed in a toolbar */
.bookmark-item > .toolbarbutton-text  { display: none !important; }

/* greyscale bookmark icons*/
.bookmark-item > .toolbarbutton-icon {
  filter: invert(1) saturate(2) brightness(.35) hue-rotate(180deg) grayscale(.95) saturate(2) brightness(2);
}

/* Remove the forward button */
#forward-button  { display: none !important; }

/* Removes the tree tab big fat header */
#sidebar-box #sidebar-header {
  visibility: collapse;
}


/* scrollbar dark  hook */
#alltabs-button {
  -moz-binding: url(data:text/xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIj8+DQo8IS0tIENvcHlyaWdodCAoYykgMjAxNyBIYWdnYWkgTnVjaGkNCkF2YWlsYWJsZSBmb3IgdXNlIHVuZGVyIHRoZSBNSVQgTGljZW5zZToNCmh0dHBzOi8vb3BlbnNvdXJjZS5vcmcvbGljZW5zZXMvTUlUDQogLS0+DQoNCjwhLS0gUnVuIHVzZXJDaHJvbWUuanMvdXNlckNocm9tZS54dWwgYW5kIC51Yy5qcy8udWMueHVsLy5jc3MgZmlsZXMgIC0tPg0KPGJpbmRpbmdzIHhtbG5zPSJodHRwOi8vd3d3Lm1vemlsbGEub3JnL3hibCI+DQogICAgPGJpbmRpbmcgaWQ9ImpzIiBleHRlbmRzPSJjaHJvbWU6Ly9nbG9iYWwvY29udGVudC9iaW5kaW5ncy90b29sYmFyYnV0dG9uLnhtbCNtZW51Ij4NCiAgICAgICAgPGltcGxlbWVudGF0aW9uPg0KICAgICAgICAgICAgPGNvbnN0cnVjdG9yPjwhW0NEQVRBWw0KICAgICAgICAgICAgICAgIGlmKHdpbmRvdy51c2VyQ2hyb21lSnNNb2QpIHJldHVybjsNCiAgICAgICAgICAgICAgICB3aW5kb3cudXNlckNocm9tZUpzTW9kID0gdHJ1ZTsNCiAgICAgICAgICAgICAgICANCiAgICAgICAgICAgICAgICB2YXIgY2hyb21lRmlsZXMgPSBGaWxlVXRpbHMuZ2V0RGlyKCJVQ2hybSIsIFtdKS5kaXJlY3RvcnlFbnRyaWVzOw0KICAgICAgICAgICAgICAgIHZhciB4dWxGaWxlcyA9IFtdOw0KICAgICAgICAgICAgICAgIHZhciBzc3MgPSBDY1snQG1vemlsbGEub3JnL2NvbnRlbnQvc3R5bGUtc2hlZXQtc2VydmljZTsxJ10uZ2V0U2VydmljZShDaS5uc0lTdHlsZVNoZWV0U2VydmljZSk7DQogICAgICAgICAgICAgICAgDQogICAgICAgICAgICAgICAgd2hpbGUoY2hyb21lRmlsZXMuaGFzTW9yZUVsZW1lbnRzKCkpIHsNCiAgICAgICAgICAgICAgICAgICAgdmFyIGZpbGUgPSBjaHJvbWVGaWxlcy5nZXROZXh0KCkuUXVlcnlJbnRlcmZhY2UoQ2kubnNJRmlsZSk7DQogICAgICAgICAgICAgICAgICAgIHZhciBmaWxlVVJJID0gU2VydmljZXMuaW8ubmV3RmlsZVVSSShmaWxlKTsNCiAgICAgICAgICAgICAgICAgICAgDQogICAgICAgICAgICAgICAgICAgIGlmKGZpbGUuaXNGaWxlKCkpIHsNCiAgICAgICAgICAgICAgICAgICAgICAgIGlmKC8oXnVzZXJDaHJvbWV8XC51YylcLmpzJC9pLnRlc3QoZmlsZS5sZWFmTmFtZSkpIHsNCiAgICAgICAgICAgICAgICAgICAgICAgICAgICBTZXJ2aWNlcy5zY3JpcHRsb2FkZXIubG9hZFN1YlNjcmlwdFdpdGhPcHRpb25zKGZpbGVVUkkuc3BlYywge3RhcmdldDogd2luZG93LCBpZ25vcmVDYWNoZTogdHJ1ZX0pOw0KICAgICAgICAgICAgICAgICAgICAgICAgfQ0KICAgICAgICAgICAgICAgICAgICAgICAgZWxzZSBpZigvKF51c2VyQ2hyb21lfFwudWMpXC54dWwkL2kudGVzdChmaWxlLmxlYWZOYW1lKSkgew0KICAgICAgICAgICAgICAgICAgICAgICAgICAgIHh1bEZpbGVzLnB1c2goZmlsZVVSSS5zcGVjKTsNCiAgICAgICAgICAgICAgICAgICAgICAgIH0NCiAgICAgICAgICAgICAgICAgICAgICAgIGVsc2UgaWYoL1wuYXNcLmNzcyQvaS50ZXN0KGZpbGUubGVhZk5hbWUpKSB7DQogICAgICAgICAgICAgICAgICAgICAgICAgICAgaWYoIXNzcy5zaGVldFJlZ2lzdGVyZWQoZmlsZVVSSSwgc3NzLkFHRU5UX1NIRUVUKSkNCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgc3NzLmxvYWRBbmRSZWdpc3RlclNoZWV0KGZpbGVVUkksIHNzcy5BR0VOVF9TSEVFVCk7DQogICAgICAgICAgICAgICAgICAgICAgICB9DQogICAgICAgICAgICAgICAgICAgICAgICBlbHNlIGlmKC9eKD8hKHVzZXJDaHJvbWV8dXNlckNvbnRlbnQpXC5jc3MkKS4rXC5jc3MkL2kudGVzdChmaWxlLmxlYWZOYW1lKSkgew0KICAgICAgICAgICAgICAgICAgICAgICAgICAgIGlmKCFzc3Muc2hlZXRSZWdpc3RlcmVkKGZpbGVVUkksIHNzcy5VU0VSX1NIRUVUKSkNCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgc3NzLmxvYWRBbmRSZWdpc3RlclNoZWV0KGZpbGVVUkksIHNzcy5VU0VSX1NIRUVUKTsNCiAgICAgICAgICAgICAgICAgICAgICAgIH0NCiAgICAgICAgICAgICAgICAgICAgfQ0KICAgICAgICAgICAgICAgIH0NCiAgICAgICAgICAgICAgICANCiAgICAgICAgICAgICAgICBzZXRUaW1lb3V0KGZ1bmN0aW9uIGxvYWRYVUwoKSB7DQogICAgICAgICAgICAgICAgICAgIGlmKHh1bEZpbGVzLmxlbmd0aCA+IDApIHsNCiAgICAgICAgICAgICAgICAgICAgICAgIGRvY3VtZW50LmxvYWRPdmVybGF5KHh1bEZpbGVzLnNoaWZ0KCksIG51bGwpOw0KICAgICAgICAgICAgICAgICAgICAgICAgc2V0VGltZW91dChsb2FkWFVMLCA1KTsNCiAgICAgICAgICAgICAgICAgICAgfQ0KICAgICAgICAgICAgICAgIH0sIDApOw0KICAgICAgICAgICAgXV0+PC9jb25zdHJ1Y3Rvcj4NCiAgICAgICAgPC9pbXBsZW1lbnRhdGlvbj4NCiAgICA8L2JpbmRpbmc+DQo8L2JpbmRpbmdzPg==);
} 
```
