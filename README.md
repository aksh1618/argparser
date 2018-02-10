# argparser

## Features

Supports positional and optional arguments, and more features, like:
- Arguments can be added with specific attributes:
    - `alias` (to add short name for argument)
    - `required` (to make argument compulsory)
    - `type` (to specify type of value for argument)
    - `nvals` (to specify number of values for argument)
    - `set_value` (to specify value to be set on argument use)
- Multiple values can be passed for argument
- Values passed on call can be accessed as a dictionary in:
    - Long form (all arguments)
    - Short form (excluding arguments with none value)
- Values can be printed in JSON format

## Usage

- Import argparser.
- Create an instance of `Parser` class.
    - Use `add_arg` method to add arguments to process.
    - Use `make_args_exclusive` method to make arguments exclusive.
    - Use `print_usage` method to print usage of the added arguments.
    - Use `parse` method to parse the arguments.
    - Use `get_values` method to get a dict of arguments and values.
    - Use `get_non_none_values` method to get a dict of only those arguments which have values.
- Use `print_json` function to print a json of the non-none values.

## Example

``` python
>>> import argparser
>>> parser = argparser.Parser()
>>> parser.add_arg('command', type=str)
>>> parser.add_arg('subcommand', type=str)
>>> parser.add_arg('--keys', type=int, nvals=2, required=True)
>>> parser.add_arg('--verbose', '-V', setval=True)
>>> parser.add_arg('--local', setval=True)
>>> parser.add_arg('--remote', setval=True)
>>> parser.make_args_exclusive('--local', '--remote')
>>> parser.parse('alpha beta --keys 1 2 -V')
>>> argparser.print_json(parser)
{"command": "alpha", "subcommand": "beta", "keys": [1, 2], "verbose": true}
```

This project was created as a part of [Project Omega](https://github.com/aksh1618/project-omega).