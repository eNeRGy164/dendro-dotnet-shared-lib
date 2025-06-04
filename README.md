# DendroDocs.Shared

[![Nuget][NUGET_BADGE]][NUGET_FEED] [![Coverage Status](https://coveralls.io/repos/github/eNeRGy164/dendro-dotnet-shared-lib/badge.svg?branch=main)](https://coveralls.io/github/eNeRGy164/dendro-dotnet-shared-lib?branch=main)

**DendroDocs.Shared** is a shared library used across multiple components of the DendroDocs ecosystem.
It provides common utilities, abstractions, and extensions that are essential for the functionality of tools like [DendroDocs.Tool](https://github.com/dendrodocs/dotnet-tool) and other .NET-based projects using DendroDocs.

## Features

* **Data Models**: Comprehensive data models for representing .NET code structure including types, methods, properties, fields, and documentation comments
* **Code Analysis**: Tools for parsing and representing .NET code elements with support for modifiers, attributes, and inheritance
* **JSON Serialization**: Optimized JSON serialization utilities with custom converters for efficient data exchange
* **String Extensions**: Helper methods for namespace and class name manipulation
* **Statement Representations**: Models for control flow statements like if/else, switch, and foreach
* **Documentation Parsing**: XML documentation comment parsing with support for all standard tags

## Prerequisites

.NET 8.0 SDK or newer.

## Installation

To use **DendroDocs.Shared** in your project, install it as a NuGet package:

```shell
dotnet add package DendroDocs.Shared
```

## Example usage:

```csharp
using DendroDocs;
using DendroDocs.Extensions;
using DendroDocs.Json;
using Newtonsoft.Json;

// Working with type descriptions
var types = new List<TypeDescription>();

// Example: Creating a type description
var classType = new TypeDescription(TypeType.Class, "MyNamespace.MyClass");

// Using string extensions for namespace manipulation
var className = "MyNamespace.MyClass".ClassName(); // Returns "MyClass"
var namespaceName = "MyNamespace.MyClass".Namespace(); // Returns "MyNamespace"

// JSON serialization with optimized settings
var serializerSettings = JsonDefaults.SerializerSettings();
var json = JsonConvert.SerializeObject(types.OrderBy(t => t.FullName), serializerSettings);

// Parsing documentation comments
var xmlDoc = @"<summary>This is a summary</summary>";
var docComments = DocumentationCommentsDescription.Parse(xmlDoc);
Console.WriteLine(docComments?.Summary); // Outputs: "This is a summary"
```

## Library Components

### Data Models (`DendroDocs` namespace)

The library provides comprehensive data models for representing .NET code structure:

- **`TypeDescription`**: Represents classes, interfaces, structs, enums, and delegates with their members
- **`MethodDescription`**: Represents methods with parameters, return types, and method body statements  
- **`PropertyDescription`**: Represents properties with getters and setters
- **`FieldDescription`**: Represents fields and constants
- **`ConstructorDescription`**: Represents class constructors
- **`EventDescription`**: Represents events and event handlers
- **`AttributeDescription`**: Represents attributes applied to code elements
- **`DocumentationCommentsDescription`**: Represents parsed XML documentation comments

### String Extensions (`DendroDocs.Extensions` namespace)

Utility methods for working with fully qualified type names:

- **`ClassName()`**: Extracts the class name from a fully qualified name
- **`Namespace()`**: Extracts the namespace from a fully qualified name  
- **`NamespaceParts()`**: Splits a namespace into its component parts

### JSON Utilities (`DendroDocs.Json` namespace)

Optimized JSON serialization for DendroDocs data models:

- **`JsonDefaults`**: Provides pre-configured settings for both Newtonsoft.Json and System.Text.Json
- **`SkipEmptyCollectionsContractResolver`**: Custom contract resolver to optimize JSON output
- **`ConcreteTypeConverter`**: Handles polymorphic type serialization

### Statement Models (`DendroDocs` namespace)

Represents control flow and code statements:

- **`Statement`**: Base class for all statement types
- **`If`** / **`IfElseSection`**: Conditional statements
- **`Switch`** / **`SwitchSection`**: Switch statements  
- **`ForEach`**: Iteration statements
- **`InvocationDescription`**: Method and property invocations
- **`AssignmentDescription`**: Variable assignments
- **`ReturnDescription`**: Return statements


# The DendroDocs Ecosystem

**DendroDocs.Shared** is a crucial part of the broader DendroDocs ecosystem.
Explore [DendroDocs](https://github.com/dendrodocs) to find more tools, libraries, and documentation resources that help you bridge the gap between your code and its documentation.

## LivingDocumentation

This shared library consolidates the following libraries previously part of [Living Documentation](https://github.com/eNeRGy164/LivingDocumentation):

* LivingDocumentation.Descriptions
* LivingDocumentation.Extensions
* LivingDocumentation.Abstractions
* LivingDocumentation.Statements

These libraries have been combined and restructured for better modularity and ease of use in the DendroDocs ecosystem.

## Contributing

Contributions are welcome! Please feel free to create [issues](https://github.com/eNeRGy164/dendro-dotnet-shared-lib/issues) or [pull requests](https://github.com/eNeRGy164/dendro-dotnet-shared-lib/pulls).

## License

This project is licensed under the [MIT License](./LICENSE).

[NUGET_BADGE]: https://img.shields.io/nuget/v/DendroDocs.Shared.svg?style=plastic
[NUGET_FEED]: https://www.nuget.org/packages/DendroDocs.Shared/
