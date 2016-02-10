# Why do we need this fork?

Castle.Core-log4net has a dependency on the exact version of log4net - 1.2.10. This makes it hard to use Castle.Logging with our projects which reference more recent version of log4net (>2.0). In this fork we will update Castle.Core references to use the most recent version of log4net. The package will be published only with NET45 support.

# Castle Core

<img align="right" src="docs/images/castle-logo.png">

Castle Core provides common Castle Project abstractions including logging services. It also features **Castle DynamicProxy** a lightweight runtime proxy generator, and **Castle DictionaryAdapter**.

See the [documentation](docs/README.md).

## Releases

See the [Releases](https://github.com/castleproject/Core/releases).

## License

Castle Core is &copy; 2004-2015 Castle Project. It is free software, and may be redistributed under the terms of the [Apache 2.0](http://opensource.org/licenses/Apache-2.0) license.

## Building

### .NET Framework and Silverlight

```
msbuild /p:Configuration=NET45-Release /t:RunAllTests buildscripts/Build.proj
msbuild /p:Configuration=NET40-Release /t:RunAllTests buildscripts/Build.proj
msbuild /p:Configuration=NET35-Release /t:RunAllTests buildscripts/Build.proj
msbuild /p:Configuration=SL50-Release /t:RunAllTests buildscripts/Build.proj
msbuild /p:Configuration=SL40-Release /t:RunAllTests buildscripts/Build.proj
```

### Mono

Castle Core supports Mono 4.0.2+, previous 4.x releases have serious runtime bugs that cause runtime crashes. Mono 3.x releases used to work well, but are not supported.

```
xbuild /p:Configuration=NET45-Release /t:RunAllTests buildscripts/Build.proj
```

### Conditional Compilation Symbols

The following conditional compilation symbols (vertical) are currently defined for each of the build configurations (horizontal):

Symbol                          | NET35              | NET40              | NET45              | SL40               | SL50
------------------------------- | ------------------ | ------------------ | ------------------ | ------------------ | ------------------
`FEATURE_LEGACY_REFLECTION_API` | :white_check_mark: | :white_check_mark: | :no_entry_sign:    | :white_check_mark: | :white_check_mark:
`FEATURE_SERIALIZATION`         | :white_check_mark: | :white_check_mark: | :white_check_mark: | :no_entry_sign:    | :no_entry_sign:
`FEATURE_XUNITNET`              | :no_entry_sign:    | :no_entry_sign:    | :no_entry_sign:    | :no_entry_sign:    | :no_entry_sign:
`DOTNET35`                      | :white_check_mark: | :no_entry_sign:    | :no_entry_sign:    | :no_entry_sign:    | :no_entry_sign:
`DOTNET40`                      | :no_entry_sign:    | :white_check_mark: | :white_check_mark: | :no_entry_sign:    | :no_entry_sign:
`DOTNET45`                      | :no_entry_sign:    | :no_entry_sign:    | :white_check_mark: | :no_entry_sign:    | :no_entry_sign:
`SILVERLIGHT`                   | :no_entry_sign:    | :no_entry_sign:    | :no_entry_sign:    | :white_check_mark: | :white_check_mark:
`SL4`                           | :no_entry_sign:    | :no_entry_sign:    | :no_entry_sign:    | :white_check_mark: | :no_entry_sign:
`SL5`                           | :no_entry_sign:    | :no_entry_sign:    | :no_entry_sign:    | :no_entry_sign:    | :white_check_mark:

The `__MonoCS__` symbol is used only in unit tests when compiled on Mono to work around Mono defects and non-Windows differences, however we are trying to move away from platform specific symbols as much as possible.
