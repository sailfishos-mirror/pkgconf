
libpkgconf `path` module
========================

The `path` module provides functions for manipulating lists of paths in a cross-platform manner.  Notably,
it is used by the `pkgconf client` to parse the ``PKG_CONFIG_PATH``, ``PKG_CONFIG_LIBDIR`` and related environment
variables.

.. c:function:: void pkgconf_path_add(const char *text, pkgconf_list_t *dirlist)

   Adds a path node to a path list.

   :param char* text: The path text to add as a path node.
   :param pkgconf_list_t* dirlist: The path list to add the path node to.
   :return: nothing

.. c:function:: size_t pkgconf_path_split(const char *text, pkgconf_list_t *dirlist)

   Splits a given text input and inserts paths into a path list.

   :param char* text: The path text to split and add as path nodes.
   :param pkgconf_list_t* dirlist: The path list to have the path nodes added to.
   :return: number of path nodes added to the path list
   :rtype: size_t

.. c:function:: size_t pkgconf_path_build_from_environ(const char *environ, const char *fallback, pkgconf_list_t *dirlist)

   Adds the paths specified in an environment variable to a path list.  If the environment variable is not set,
   an optional default set of paths is added.

   :param char* environ: The environment variable to look up.
   :param char* fallback: The fallback paths to use if the environment variable is not set.
   :param pkgconf_list_t* dirlist: The path list to add the path nodes to.
   :return: number of path nodes added to the path list
   :rtype: size_t

.. c:function:: bool pkgconf_path_match_list(const char *path, pkgconf_list_t *dirlist)

   Checks whether a path has a matching prefix in a path list.

   :param char* path: The path to check against a path list.
   :param pkgconf_list_t* dirlist: The path list to check the path against.
   :return: true if the path list has a matching prefix, otherwise false
   :rtype: bool

.. c:function:: void pkgconf_path_free(pkgconf_list_t *dirlist)

   Releases any path nodes attached to the given path list.

   :param pkgconf_list_t* dirlist: The path list to clean up.
   :return: nothing