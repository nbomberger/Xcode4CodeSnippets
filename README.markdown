# Xcode 4 Code Snippets

This is the collection of my user-defined code snippets for Xcode 4. Free feel to add them to your own collection.

## Install

* Clone, fork or [download](https://github.com/nbomberger/Xcode4CodeSnippets/zipball/master) this collection of code snippets.
* Copy the code snippet files to: `~/Library/Developer/Xcode/UserData/CodeSnippets`

### Hint

To make life easier for me, I clone this repo to my CodeSnippets directory. This makes it easier for me to keep this repo up to date and simplifies sharing my code snippets across multiple machines. You can do the same, but I recommend forking this repo first so you can store your own code snippets along with the ones in this collection.

Some of these snippets are from github user kirbyt and others are from this post [Xcode Snippets](http://www.icodeblog.com/2011/12/06/using-xcode-4-snippets/)

# Code Snippet Listing <a id="codesnippetlisting"></a>

This markdown is totally borrowed from kirbyt with small edits.

Each code snippet shortcut is prefixed with **wps** to avoid conflict with other shortcuts. This also groups the code snippets in the Code Completion window.
## Synthesize
**Shortcut**: wpsSynthesize  
**File**: [004CE6E9-88B2-4F67-B4F8-2511884A0968.codesnippet](http://github.com/kirbyt/Xcode4CodeSnippets/blob/master/004CE6E9-88B2-4F67-B4F8-2511884A0968.codesnippet)  
**Scope**: ClassImplementation  
**Summary**: Synthesize property.  

    @synthesize <#property#> = _<#ivar#>;  

## UITableView Stub
**Shortcut**: wpsTable  
**File**: [08FBEC3D-4375-4E86-9B01-DE3492CF0B02.codesnippet](http://github.com/kirbyt/Xcode4CodeSnippets/blob/master/08FBEC3D-4375-4E86-9B01-DE3492CF0B02.codesnippet)  
**Scope**: ClassImplementation  
**Summary**: UITableView data and delegate method stubs.  

    #pragma mark - UITableViewDataSource and UITableViewDelegate methods  
      
    - (NSInteger)numberOfSectionsInTableView:(UITableView *)tableView  
    {  
       NSInteger count = 1;  
       return count;  
    }  
      
    - (NSInteger)tableView:(UITableView *)tableView numberOfRowsInSection:(NSInteger)section  
    {  
       NSInteger count = 0;  
       return count;  
    }  
      
    - (NSString *)tableView:(UITableView *)tableView titleForHeaderInSection:(NSInteger)section  
    {  
       return @"Header Title";  
    }  
      
    - (UITableViewCell *)tableView:(UITableView *)tableView cellForRowAtIndexPath:(NSIndexPath *)indexPath  
    {  
       static NSString *cellID = @"cellID";  
       UITableViewCell *cell = [tableView dequeueReusableCellWithIdentifier:cellID];  
       if (!cell) {  
          cell = [[UITableViewCell alloc] initWithStyle:UITableViewCellStyleDefault reuseIdentifier:cellID];  
       }  
         
       NSString *text =[NSString stringWithFormat:@"Row %i", [indexPath row]];  
       [[cell textLabel] setText:text];  
         
       return cell;  
    }  
      
    - (void)tableView:(UITableView *)tableView didSelectRowAtIndexPath:(NSIndexPath *)indexPath  
    {  
       [tableView deselectRowAtIndexPath:indexPath animated:YES];  
    }  
      

## DLog #define Statements
**Shortcut**: wpsDLog  
**File**: [21B87E09-B160-4DA9-85A6-67AB236A2F54.codesnippet](http://github.com/kirbyt/Xcode4CodeSnippets/blob/master/21B87E09-B160-4DA9-85A6-67AB236A2F54.codesnippet)  
**Scope**: TopLevel  
**Summary**: Defines the DLog statements for the pre-compiled header.  

    #ifdef DEBUG  
       #define DLog(...) NSLog(@"%s %@", __PRETTY_FUNCTION__, [NSString stringWithFormat:__VA_ARGS__])  
       #define ALog(...) [[NSAssertionHandler currentHandler] handleFailureInFunction:[NSString stringWithCString:__PRETTY_FUNCTION__ encoding:NSUTF8StringEncoding] file:[NSString stringWithCString:__FILE__ encoding:NSUTF8StringEncoding] lineNumber:__LINE__ description:__VA_ARGS__]  
    #else  
       #define DLog(...) do { } while (0)  
       #ifndef NS_BLOCK_ASSERTIONS  
          #define NS_BLOCK_ASSERTIONS  
       #endif  
       #define ALog(...) NSLog(@"%s %@", __PRETTY_FUNCTION__, [NSString stringWithFormat:__VA_ARGS__])  
    #endif  
      
    #define ZAssert(condition, ...) do { if (!(condition)) { ALog(__VA_ARGS__); }} while(0)  
      

## Class Extension
**Shortcut**: wpsClassExtension  
**File**: [220BFE9F-59FE-4179-8E5A-759ACD66F1CC.codesnippet](http://github.com/kirbyt/Xcode4CodeSnippets/blob/master/220BFE9F-59FE-4179-8E5A-759ACD66F1CC.codesnippet)  
**Scope**: TopLevel  
**Summary**: Creates a class externsion.  

    @interface <#name#> ()  
    <#property or method#>  
    @end  
      

## Property Assign
**Shortcut**: wpsPropertyAssign  
**File**: [2A05C797-72E5-4890-A7CB-2C8A6EF193A5.codesnippet](http://github.com/kirbyt/Xcode4CodeSnippets/blob/master/2A05C797-72E5-4890-A7CB-2C8A6EF193A5.codesnippet)  
**Scope**: All  
**Summary**: Defines a declared property.  

    @property (nonatomic, assign) <#type#> <#variable#>;  

## MIT License Statement
**Shortcut**: mit  
**File**: [32D765A1-3B1E-4A88-A13D-F9B4CEB926A5.codesnippet](http://github.com/kirbyt/Xcode4CodeSnippets/blob/master/32D765A1-3B1E-4A88-A13D-F9B4CEB926A5.codesnippet)  
**Scope**: TopLevel  
**Summary**: File header comment.  

    /**  
     **   <#name#>  
     **  
     **   Created by Kirby Turner.  
     **   Copyright (c) 2012 White Peak Software. All rights reserved.  
     **  
     **   Permission is hereby granted, free of charge, to any person obtaining   
     **   a copy of this software and associated documentation files (the   
     **   "Software"), to deal in the Software without restriction, including   
     **   without limitation the rights to use, copy, modify, merge, publish,   
     **   distribute, sublicense, and/or sell copies of the Software, and to permit   
     **   persons to whom the Software is furnished to do so, subject to the   
     **   following conditions:  
     **  
     **   The above copyright notice and this permission notice shall be included   
     **   in all copies or substantial portions of the Software.  
     **  
     **   THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS   
     **   OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF   
     **   MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.   
     **   IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY   
     **   CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,   
     **   TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE   
     **   SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.  
     **  
     **/  
      

## Property Strong
**Shortcut**: wpsProperty  
**File**: [3357A88A-4687-4AC1-BE42-9BE3ACE61B53.codesnippet](http://github.com/kirbyt/Xcode4CodeSnippets/blob/master/3357A88A-4687-4AC1-BE42-9BE3ACE61B53.codesnippet)  
**Scope**: All  
**Summary**: Defines a declared property.  

    @property (nonatomic, strong) <#type#> *<#variable#>;  

## PerformSelector Leak
**Shortcut**: wpsPerformSelectorLeak  
**File**: [64A56053-8AA1-43C0-A89F-5916D8212A06.codesnippet](http://github.com/kirbyt/Xcode4CodeSnippets/blob/master/64A56053-8AA1-43C0-A89F-5916D8212A06.codesnippet)  
**Scope**: CodeBlock  
**Summary**: #pragram to ignore PerformSelector leark warning.  

    #pragma clang diagnostic push  
    #pragma clang diagnostic ignored "-Warc-performSelector-leaks"  
    <#[target performSelector]#>  
    #pragma clang diagnostic pop  
      

## initWithDefaultNib
**Shortcut**: wpsInitWithDefaultNib  
**File**: [796A1936-1B22-43E8-B0D4-E7EAA939CFD1.codesnippet](http://github.com/kirbyt/Xcode4CodeSnippets/blob/master/796A1936-1B22-43E8-B0D4-E7EAA939CFD1.codesnippet)  
**Scope**: ClassImplementation  
**Summary**: initWithDefaultNib method stub.  

    - (id)initWithDefaultNib  
    {  
       self = [super initWithNibName:@"<#nibname#>" bundle:nil];  
       if (self) {  
          <#initializations#>  
       }  
       return self;  
    }  
      

## initWithDefaultNib Declaration
**Shortcut**: wpsInitWithDefaultNib  
**File**: [E811EA70-B05F-4799-89D7-943CAF92AB1D.codesnippet](http://github.com/kirbyt/Xcode4CodeSnippets/blob/master/E811EA70-B05F-4799-89D7-943CAF92AB1D.codesnippet)  
**Scope**: ClassInterfaceMethods  
**Summary**: Declares - (id)initWithDefaultNib method.  

    - (id)initWithDefaultNib;  

## IBOutlet Property
**Shortcut**: wpsIBOutlet  
**File**: [E996CD71-CF1E-4A4E-AF95-C7B5BBE2BCA3.codesnippet](http://github.com/kirbyt/Xcode4CodeSnippets/blob/master/E996CD71-CF1E-4A4E-AF95-C7B5BBE2BCA3.codesnippet)  
**Scope**: ClassInterfaceMethods  
**Summary**: Defines a declared property outlet.  

    @property (nonatomic, strong) IBOutlet <#type#> *<#variable#>;  

## initWithDefaultWindowNib Declaration
**Shortcut**: wpsInitWithDefaultWindowNib  
**File**: [EA4152C2-16A8-4B05-A319-6BA5DD92ADA8.codesnippet](http://github.com/kirbyt/Xcode4CodeSnippets/blob/master/EA4152C2-16A8-4B05-A319-6BA5DD92ADA8.codesnippet)  
**Scope**: ClassImplementation  
**Summary**: initWithDefaultWindowNib method stub for Mac.  

    - (id)initWithDefaultWindowNib  
    {  
       self = [super initWithWindowNibName:@"<#NibName#>"];  
       if (self) {  
          <#initializations#>  
       }  
       return self;  
    }  
      
    
# lscs.py Script

`lscs.py` is a python script that lists the code snippets for the current user. The listing shows the title, shortcut, and summary for each code snippet file.

    Example: python lscs.py

`lscs.py` is also used to create the [code snippet listing](#codesnippetlisting) shown above. You can do the same by using the `-f markdown` (or `--format=markdown`) command line parameter.

    Example: python lscs.py --f markdown

# Support, Bugs and Feature requests

There is absolutely no support offered for this collection of code snippets. You're on your own! However, free feel to send me a message or even a pull request if you have an interesting and useful code snippet to share.

# License

The MIT License  

Copyright (c) 2012 White Peak Software Inc

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
