# Pip-compile error

```bash
pip install pip-tools
```

Now, execution of `pip-compile -v` results in tensorflow not being found.

```
ERROR: Could not find a version that satisfies the requirement tensorflow~=2.13 (from versions: 2.16.0rc0)
```

## Full stacktrace

```text
$ pip-compile -v
Using pip-tools configuration defaults found in 'pyproject.toml'.
Creating venv isolated environment...
Installing packages in isolated environment... (setuptools)
Getting build dependencies for wheel...
running egg_info
writing flypenguin_resolver_test.egg-info/PKG-INFO
writing dependency_links to flypenguin_resolver_test.egg-info/dependency_links.txt
writing requirements to flypenguin_resolver_test.egg-info/requires.txt
writing top-level names to flypenguin_resolver_test.egg-info/top_level.txt
reading manifest file 'flypenguin_resolver_test.egg-info/SOURCES.txt'
writing manifest file 'flypenguin_resolver_test.egg-info/SOURCES.txt'
Installing packages in isolated environment... (wheel)
Getting metadata for wheel...
running dist_info
creating /var/folders/s_/9f5bhljn2256wyc989strhqh0000gn/T/tmp1m5kzdra/flypenguin_resolver_test.egg-info
writing /var/folders/s_/9f5bhljn2256wyc989strhqh0000gn/T/tmp1m5kzdra/flypenguin_resolver_test.egg-info/PKG-INFO
writing dependency_links to /var/folders/s_/9f5bhljn2256wyc989strhqh0000gn/T/tmp1m5kzdra/flypenguin_resolver_test.egg-info/dependency_links.txt
writing requirements to /var/folders/s_/9f5bhljn2256wyc989strhqh0000gn/T/tmp1m5kzdra/flypenguin_resolver_test.egg-info/requires.txt
writing top-level names to /var/folders/s_/9f5bhljn2256wyc989strhqh0000gn/T/tmp1m5kzdra/flypenguin_resolver_test.egg-info/top_level.txt
writing manifest file '/var/folders/s_/9f5bhljn2256wyc989strhqh0000gn/T/tmp1m5kzdra/flypenguin_resolver_test.egg-info/SOURCES.txt'
reading manifest file '/var/folders/s_/9f5bhljn2256wyc989strhqh0000gn/T/tmp1m5kzdra/flypenguin_resolver_test.egg-info/SOURCES.txt'
writing manifest file '/var/folders/s_/9f5bhljn2256wyc989strhqh0000gn/T/tmp1m5kzdra/flypenguin_resolver_test.egg-info/SOURCES.txt'
creating '/var/folders/s_/9f5bhljn2256wyc989strhqh0000gn/T/tmp1m5kzdra/flypenguin_resolver_test-1.0.0.dist-info'
Using indexes:
  https://pypi.org/simple

                          ROUND 1
  ERROR: Could not find a version that satisfies the requirement tensorflow~=2.13 (from versions: 2.16.0rc0)
  1 # Pip-compile error
Traceback (most recent call last):
  1 # Pip-compile error
  File "/usr/local/lib/python3.12/site-packages/pip/_vendor/resolvelib/resolvers.py", line 397, in resolve
    self._add_to_criteria(self.state.criteria, r, parent=None)
  File "/usr/local/lib/python3.12/site-packages/pip/_vendor/resolvelib/resolvers.py", line 174, in _add_to_criteria
    raise RequirementsConflicted(criterion)
pip._vendor.resolvelib.resolvers.RequirementsConflicted: Requirements conflict: SpecifierRequirement('tensorflow~=2.13')

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/local/lib/python3.12/site-packages/pip/_internal/resolution/resolvelib/resolver.py", line 95, in resolve
    result = self._result = resolver.resolve(
                            ^^^^^^^^^^^^^^^^^
  File "/usr/local/lib/python3.12/site-packages/pip/_vendor/resolvelib/resolvers.py", line 546, in resolve
    state = resolution.resolve(requirements, max_rounds=max_rounds)
            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/local/lib/python3.12/site-packages/pip/_vendor/resolvelib/resolvers.py", line 399, in resolve
    raise ResolutionImpossible(e.criterion.information)
pip._vendor.resolvelib.resolvers.ResolutionImpossible: [RequirementInformation(requirement=SpecifierRequirement('tensorflow~=2.13'), parent=None)]

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "/usr/local/bin/pip-compile", line 8, in <module>
    sys.exit(cli())
             ^^^^^
  File "/usr/local/Cellar/pip-tools/7.4.1/libexec/lib/python3.12/site-packages/click/core.py", line 1157, in __call__
    return self.main(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/local/Cellar/pip-tools/7.4.1/libexec/lib/python3.12/site-packages/click/core.py", line 1078, in main
    rv = self.invoke(ctx)
         ^^^^^^^^^^^^^^^^
  File "/usr/local/Cellar/pip-tools/7.4.1/libexec/lib/python3.12/site-packages/click/core.py", line 1434, in invoke
    return ctx.invoke(self.callback, **ctx.params)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/local/Cellar/pip-tools/7.4.1/libexec/lib/python3.12/site-packages/click/core.py", line 783, in invoke
    return __callback(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/local/Cellar/pip-tools/7.4.1/libexec/lib/python3.12/site-packages/click/decorators.py", line 33, in new_func
    return f(get_current_context(), *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/local/Cellar/pip-tools/7.4.1/libexec/lib/python3.12/site-packages/piptools/scripts/compile.py", line 470, in cli
    results = resolver.resolve(max_rounds=max_rounds)
              ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/local/Cellar/pip-tools/7.4.1/libexec/lib/python3.12/site-packages/piptools/resolver.py", line 604, in resolve
    is_resolved = self._do_resolve(
                  ^^^^^^^^^^^^^^^^^
  File "/usr/local/Cellar/pip-tools/7.4.1/libexec/lib/python3.12/site-packages/piptools/resolver.py", line 636, in _do_resolve
    resolver.resolve(
  File "/usr/local/lib/python3.12/site-packages/pip/_internal/resolution/resolvelib/resolver.py", line 104, in resolve
    raise error from e
pip._internal.exceptions.DistributionNotFound: No matching distribution found for tensorflow~=2.13
```

