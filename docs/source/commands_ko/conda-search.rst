
.. _search_ref:

conda search
=======================

.. raw:: html

   <PRE>
   <!-- Manpage converted by man2html 3.0.1 -->
   <B>CONDA(1)</B>                         User Commands                        <B>CONDA(1)</B>
   
   
   
   
   </PRE>
   <H2>NAME</H2><PRE>
          conda - conda search
   
   
   </PRE>
   <H2>DESCRIPTION</H2><PRE>
          usage: conda search [-h] [-n ENVIRONMENT | <B>-p</B> PATH] [--canonical] [-f]
   
          [--names-only] [--use-index-cache] [-o]
                 [--platform  {win-32,win-64,osx-64,linux-32,linux-64}]  [--spec]
                 [--reverse-dependency]   [--offline]   [-c   CHANNEL]   [--over-
                 ride-channels] [--json] [--debug] [--verbose] [--use-local] [-k]
                 [regex]
   
          Search for packages and display  their  information.  The  input  is  a
          Python  regular  expression.   To perform a search with a search string
          that starts with a -, separate the search from  the  options  with  <B>--</B>,
          like 'conda search <B>--</B> <B>-h</B>'.
   
          A * in the results means that package is installed in the current envi-
          ronment. A . means that package is not installed but is cached  in  the
          pkgs directory.
   
   
   </PRE>
   <H2>OPTIONS</H2><PRE>
      <B>positional</B> <B>arguments:</B>
          regex  Package specification or Python regular expression to search for
                 (default: display all packages).
   
      <B>optional</B> <B>arguments:</B>
          <B>-h</B>, <B>--help</B>
                 Show this help message and exit.
   
          <B>-n</B> ENVIRONMENT, <B>--name</B> ENVIRONMENT
                 Name of environment (in envs dirs).
   
          <B>-p</B> PATH, <B>--prefix</B> PATH
                 Full  path   to   environment   prefix   (default:   <I>root</I>   <I>pre-</I>
                 <I>fix/envs/conda-docs</I>).
   
          <B>--canonical</B>
                 Output canonical names of packages only.
   
          <B>-f</B>, <B>--full-name</B>
                 Only search for full name, ie. ^&lt;regex&gt;$.
   
          <B>--names-only</B>
                 Output only package names.
   
          <B>--use-index-cache</B>
                 Use cache of channel index files.
   
          <B>-o</B>, <B>--outdated</B>
                 Only display installed but outdated packages.
   
          <B>--platform</B> {win-32,win-64,osx-64,linux-32,linux-64}
                 Search  the  given  platform. Should be formatted like 'osx-64',
                 'linux-32', 'win-64', and so on. The default is  to  search  the
                 current platform.
   
          <B>--spec</B> Treat  the  regex  argument  as  a package specification instead
                 (package_name[=version[=build]]).
   
          <B>--reverse-dependency</B>
                 Perform a reverse dependency search. When using this  flag,  the
                 <B>--full-name</B> flag is recommended. Use 'conda info package' to see
                 the dependencies of a package.
   
          <B>--offline</B>
                 Offline mode, don't connect to the Internet.
   
          <B>-c</B> CHANNEL, <B>--channel</B> CHANNEL
                 Additional channel  to  search  for  packages.  These  are  URLs
                 searched  in  the  order  they  are given (including file:// for
                 local directories). Then, the defaults or channels from .condarc
                 are  searched (unless <B>--override-channels</B> is given). You can use
                 'defaults' to get the default packages for conda,  and  'system'
                 to  get  the  system  packages,  which  also takes .condarc into
                 account. You can also  use  any  name  and  the  .condarc  chan-
                 nel_alias  value will be prepended. The default channel_alias is
                 http://conda.anaconda.org/.
   
          <B>--override-channels</B>
                 Do not search default or .condarc channels. Requires  <B>--channel</B>.
   
          <B>--json</B> Report all output as json. Suitable for using conda programmati-
                 cally.
   
          <B>--debug</B>
                 Show debug output.
   
          <B>--verbose</B>, <B>-v</B>
                 Use once for info, twice for debug, three times for trace.
   
          <B>--use-local</B>
                 Use locally built packages.
   
          <B>-k</B>, <B>--insecure</B>
                 Allow conda to perform "insecure"  SSL  connections  and  trans-
                 fers.Equivalent to setting 'ssl_verify' to 'false'.
   
   
   </PRE>
   <H2>EXAMPLES</H2><PRE>
          Search for packages with 'scikit' in the name:
   
                 conda search scikit
   
          Search  for  the  'python'  package  (but  no  other packages that have
          'python' in the name):
   
                 conda search -f python
   
          Search for packages for 64-bit Linux (by  default,  packages  for  your
          current platform are shown):
   
                 conda search --platform linux-64
   
   
   
   
   </PRE>
   <H2>Anaconda, Inc.                     12i 2017                           CONDA(1)</H2><PRE>
   </PRE>
