# Overview
this repo is setup for lfs tracking the following file types

* Blend
* PNG
* TGA
* JPG/JPEG
* PSD

Before commiting always run
```
git lfs status
```

To make sure the files you are comitting are tracked by git lfs. If you see files missing from your list, edit ***.gitattributes*** first.


# Editing .gitattributes

To track a file type with git lfs it is sufficient to add the following to .gitattributes

```
*.<extension> filter=lfs diff=lfs merge=lfs -text
```

For instance to track blend files with git lfs you could add the following to .gitattributes

```
*.blend filter=lfs diff=lfs merge=lfs -text
```

However this is really not sufficient. In the case of file systems that are case sensitive (linux, macos) you might have problems depending on how your git install is configured. 

In that situation the above filter would not allow git-lfs to track the following file

```
mygreatmodel.Blend
```

or

```
mygreatmodel.BLEND
```

or even

```
mygreatmodel.BlEnD
```

So instead add the following pattern to .gitattributes to track blend files

```
*.[bB][lL][eE][nN][dD] filter=lfs diff=lfs merge=lfs -text
```

With this filter git lfs will track any combination of upper and lower case characters in your blender file extensions.