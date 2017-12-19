
.. _remove_ref:

conda remove
=======================

.. raw:: html

   <PRE>
   <!-- Manpage converted by man2html 3.0.1 -->
   <B>CONDA(1)</B>                         User Commands                        <B>CONDA(1)</B>
   
   
   
   
   </PRE>
   <H2>NAME</H2><PRE>
          conda - conda remove
   
   
   </PRE>
   <H2>DESCRIPTION</H2><PRE>
          usage:  conda  remove  [-h] [-y] [--dry-run] [--json] [--debug] [--ver-
          bose]
   
          [--all] [--features] [--force] [--no-pin] [-c CHANNEL]
                 [--override-channels]  [-n   ENVIRONMENT   |   <B>-p</B>   PATH]   [-q]
                 [--no-use-index-cache]     [--use-index-cache]     [--use-local]
                 [--offline] [-k] [package_name [package_name ...]]
   
          Remove a list of packages from a specified conda environment.
   
          This command will also remove any package that depends on  any  of  the
          specified  packages as well---unless a replacement can be found without
          that dependency. If you wish  to  skip  this  dependency  checking  and
          remove just the requested packages, add the '--force' option. Note how-
          ever that this may result in a broken environment,  so  use  this  with
          caution.
   
   
   </PRE>
   <H2>OPTIONS</H2><PRE>
      <B>positional</B> <B>arguments:</B>
          package_name
                 Package names to remove from the environment.
   
      <B>optional</B> <B>arguments:</B>
          <B>-h</B>, <B>--help</B>
                 Show this help message and exit.
   
          <B>-y</B>, <B>--yes</B>
                 Do not ask for confirmation.
   
          <B>--dry-run</B>
                 Only display what would have been done.
   
          <B>--json</B> Report all output as json. Suitable for using conda programmati-
                 cally.
   
          <B>--debug</B>
                 Show debug output.
   
          <B>--verbose</B>, <B>-v</B>
                 Use once for info, twice for debug, three times for trace.
   
          <B>--all</B>  Remove all packages, i.e., the entire environment.
   
          <B>--features</B>
                 Remove features (instead of packages).
   
          <B>--force</B>
                 Forces removal of  a  package  without  removing  packages  that
                 depend on it. Using this option will usually leave your environ-
                 ment in a broken and inconsistent state.
   
          <B>--no-pin</B>
                 Ignore pinned file.
   
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
   
          <B>-n</B> ENVIRONMENT, <B>--name</B> ENVIRONMENT
                 Name of environment (in envs dirs).
   
          <B>-p</B> PATH, <B>--prefix</B> PATH
                 Full   path   to   environment   prefix   (default:   <I>root</I>  <I>pre-</I>
                 <I>fix/envs/conda-docs</I>).
   
          <B>-q</B>, <B>--quiet</B>
                 Do not display progress bar.
   
          <B>--no-use-index-cache</B>
                 Force fetching of channel index files.
   
          <B>--use-index-cache</B>
                 Use cache of channel index files.
   
          <B>--use-local</B>
                 Use locally built packages.
   
          <B>--offline</B>
                 Offline mode, don't connect to the Internet.
   
          <B>-k</B>, <B>--insecure</B>
                 Allow conda to perform "insecure"  SSL  connections  and  trans-
                 fers.Equivalent to setting 'ssl_verify' to 'false'.
   
   
   </PRE>
   <H2>EXAMPLES</H2><PRE>
                 conda remove -n myenv scipy
   
   
   
   
   </PRE>
   <H2>Anaconda, Inc.                     12i 2017                           CONDA(1)</H2><PRE>
   </PRE>
