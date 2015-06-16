Coding Guidelines
========
These are my coding style & guidelines for C-style languages. It's mostly a mash-up of Allman, K&R, Kernel, and Stroustrup style with my own touches.

## Editor
[Sublime Text](http://www.sublimetext.com/) and have provided the settings I use below.

### Packages
* [Package Control](https://sublime.wbond.net/) - For managing packages. Install this first to install the rest
* [Alignment](http://wbond.net/sublime_packages/alignment) - Useful for aligning blocks of assignments, etc. Highlight text and ctrl+alt+a
* [GitGutter](http://www.jisaacks.com/gitgutter) - Shows info in the gutter area indicating whether a line has been inserted, modified or deleted
* [SublimeGit](https://sublimegit.net/) - Full-featued Git integration
* [SublimeLinter](http://www.sublimelinter.com/) - Inline lint highlighting

#### Sublime Settings
Menu: `Preferences > Settings - User`
```
{
    "auto_indent": true,
    "auto_match_enabled": false,
    "color_scheme": "Packages/Color Scheme - Default/Twilight.tmTheme",
    "custom_mouse_wheel_switches_tab": true,
    "custom_sidebar_bold_dirs": true,
    "custom_sidebar_bold_selected": true,
    "draw_indent_guides": false,
    "fold_buttons": false,
    "font_options":
    [
        "subpixel_antialias",
        "directwrite"
    ],
    "font_size": 8,
    "highlight_line": true,
    "ignored_packages":
    [
        "Vintage"
    ],
    "indent_to_bracket": true,
    "line_padding_bottom": 1,
    "line_padding_top": 1,
    "match_brackets": true,
    "match_selection": true,
    "scroll_past_end": true,
    "smart_indent": true,
    "tab_size": 4,
    "translate_tabs_to_spaces": true,
    "trim_automatic_white_space": true,
    "trim_trailing_white_space_on_save": true,
    "word_wrap": false,
    "rulers": [120]
}
```

### Coding Style

#### Indentation
- 4 characters indentation using spaces; tabs are not allowed.
- Do not put multiple statements on a single line.
- All trailing whitespace should be trimmed.


#### Long lines and string
The limit on the length of lines is 120 columns.

Statements longer than 120 columns should be broken into sensible chunks, unless exceeding 120 columns significantly
increases readability and does not hide information. Long argument lists can be broken into multiple lines, each
argument at the same indentation level as the first in the argument list. The exception to this rule are arrays, where
each element should be on the same indentation level as the first element in the array. Examples:
```php
some_func($argument1, $argument2, $argument3,
          $argument4, $argument5, $argument6);

some_func($argument1, $argument2, array('element1',
                                        'element2',
                                        'element3'));
```
#### Braces and spaces
All control blocks have their braces on a newline, with the exception of `else` `do` `try` `catch` `finally`
If the body of a control statement is empty, the opening and closing braces can be on the same line
'else', 'elseif', and 'else if' must be on a newline, and not after the closing brace of the
    preceding statement:
```php
    if ($condition < 1)
    {
    }
    else if ($condition > 1)
    {
    }
    else {
    }
```

Labels remain on the same indentation level as their parent (optional, helps excessive levels of indentation) ie:
```php
    select ($value)
    {
    case 1: ...
    }
```
- Omitting braces for single-line statements is optional.
- Closing braces must be on their own line except in the cases where it is followed by a continuation of the same statement. Such as a `do` and `else`.
- Always use a space after keywords, binary, and ternary operators: `if  switch  case  for  do  while  try  =>  =  +  -  <  >  *  /  %  |  &  ^  <=  >=  ==  !=  ?  :`
- No space after unary operators: `& * + - ~ !`
- No space before the postfix increment & decrement unary operators: `++ --`
- No space after the prefix increment & decrement unar operators: `++ --`
- No space around the `.` or `->` operators
- Do *not* add spaces around (inside) parenthesized expressions. Don't do this: `if ( some_condition )`

Align code for easier readability when possible. A common case are dictionaries, arrays, method chaining, etc. Consider the following examples in different languages:
###### C
```c
static const struct cook_operations pancake_cops = {
    .chef    = THIS_CHEF,
    .prepare = pancake_prep,
    .cook    = pancake_panfry
};
```
###### D
```d
enum {
    DRAG        = 0.47f,
    RADIUS      = 0.11938f,
    AIR_DENSITY = 1.225f,
}
```
###### PHP
```php
log(array(
    'message' => "Failed to pan-fry {$pancake}",
    'line'    => __LINE__,
    'file'    => __FILE__
), Log::ERR);
```
There are some cases where aligning can reduce readability, in these situations you should use whatever favors readability.

#### Naming
- Constants should be in UPPERCASE.
- Global variables need to have descriptive names, as do global functions. Do this: `count_active_users()` instead of `cntuser()`
- Avoid encoding the type of the function into the name (so-called Hungarian notation.) Do not do this:
    `$strName = "Beau"` instead do this `$name = "Beau"`
- Local variables should be short, and to the point.
- Function names are in lowercase, and contain and underscore between words. ie: `like_this()`, not camel-case `likeThis()`.
- Class methods have lowercase first letter, using camel-case for words. ie: `class->likeThis()`


#### Functions
- Functons should be short and sweet, and do just one thing.
- Separate functions with one blank line.
- When doing error checking try to return as early as possible.

The rationale for the last point is it reduces the amount of nesting and unconditional statements are easier to understand and follow.


#### Commenting
- Use // only for single-line comments.
- Use /* ... */ style comments for either single-line or multi-line comments.

The recommended style looks like this:
```c
/**
 * This is the style for multi-line
 * comments. Please use it consistently.
 *
 * Description:  A columns of asterisks to the left side,
 * with a beginning and ending almost-blank lines.
 */
 ```
