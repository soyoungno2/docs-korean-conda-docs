
.. _install_ref:

conda install
=======================

.. raw:: html

   <PRE>
   <!-- Manpage converted by man2html 3.0.1 -->
   <B>CONDA(1)</B>                         User Commands                        <B>CONDA(1)</B>
   
   
   
   
   </PRE>
   <H2>NAME</H2><PRE>
          conda - conda install
   
   
   </PRE>
   <H2>DESCRIPTION</H2><PRE>
          usage: conda install [-h] [--revision REVISION] [-y] [--dry-run] [-f]
   
          [--file FILE] [--no-deps] [-m] [--use-index-cache]
                 [--use-local]   [--offline]  [--no-pin]  [-c  CHANNEL]  [--over-
                 ride-channels] [-n ENVIRONMENT | <B>-p</B> PATH] [-q] [--copy] [--clob-
                 ber]       [-k]       [--alt-hint]       [--update-dependencies]
                 [--no-update-dependencies]   [--channel-priority]    [--no-chan-
                 nel-priority]   [--show-channel-urls]   [--no-show-channel-urls]
                 [--json] [--debug] [--verbose] [package_spec [package_spec ...]]
   
          Installs a list of packages into a specified conda environment.
   
          This  command  accepts  a  list  of package specifications (e.g, bitar-
          ray=0.8) and installs a set of packages consistent with those  specifi-
          cations and compatible with the underlying environment. If full compat-
          ibility cannot be assured, an error is reported and the environment  is
          not changed.
   
          Conda  attempts  to  install the newest versions of the requested pack-
          ages. To accomplish this, it may update some packages that are  already
          installed, or install additional packages. To prevent existing packages
          from updating, use the <B>--no-update-deps</B> option. This may force conda to
          install  older versions of the requested packages, and it does not pre-
          vent additional dependency packages from being installed.
   
          If you wish to skip dependency checking altogether, use  the  '--force'
          option.  This  may result in an environment with incompatible packages,
          so this option must be used with great caution.
   
          conda can also be called with a list of explicit  conda  package  file-
          names  (e.g.  ./lxml-3.2.0-py27_0.tar.bz2).  Using  conda  in this mode
          implies the <B>--force</B> option, and should likewise be used with great cau-
          tion.  Explicit filenames and package specifications cannot be mixed in
          a single command.
   
   
   </PRE>
   <H2>OPTIONS</H2><PRE>
      <B>positional</B> <B>arguments:</B>
          package_spec
                 Packages to install into the conda environment.
   
      <B>optional</B> <B>arguments:</B>
          <B>-h</B>, <B>--help</B>
                 Show this help message and exit.
   
          <B>--revision</B> REVISION
                 Revert to the specified REVISION.
   
          <B>-y</B>, <B>--yes</B>
                 Do not ask for confirmation.
   
          <B>--dry-run</B>
                 Only display what would have been done.
   
          <B>-f</B>, <B>--force</B>
                 Force install (even when  package  already  installed),  implies
                 <B>--no-deps</B>.
   
          <B>--file</B> FILE
                 Read  package versions from the given file. Repeated file speci-
                 fications can be passed (e.g. <B>--file</B>=<I>file1</I> <B>--file</B>=<I>file2</I>).
   
          <B>--no-deps</B>
                 Do not install dependencies.
   
          <B>-m</B>, <B>--mkdir</B>
                 Create the environment directory if necessary.
   
          <B>--use-index-cache</B>
                 Use cache of channel index files.
   
          <B>--use-local</B>
                 Use locally built packages.
   
          <B>--offline</B>
                 Offline mode, don't connect to the Internet.
   
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
   
          <B>--copy</B> Install all packages using copies instead of hard- or soft-link-
                 ing.
   
          <B>--clobber</B>
                 Allow  clobbering of overlapping file paths within packages, and
                 suppress related warnings.
   
          <B>-k</B>, <B>--insecure</B>
                 Allow conda to perform "insecure"  SSL  connections  and  trans-
                 fers.Equivalent to setting 'ssl_verify' to 'false'.
   
          <B>--alt-hint</B>
                 Use an alternate algorithm to generate an unsatisfiability hint.
   
          <B>--update-dependencies</B>, <B>--update-deps</B>
                 Update dependencies (default: True).
   
          <B>--no-update-dependencies</B>, <B>--no-update-deps</B>
                 Don't update dependencies (default: False).
   
          <B>--channel-priority</B>, <B>--channel-pri</B>, <B>--chan-pri</B>
                 Channel priority takes precedence over package version (default:
                 True).  Note: This feature is in beta and may change in a future
                 release.
   
          <B>--no-channel-priority</B>, <B>--no-channel-pri</B>, <B>--no-chan-pri</B>
                 Package version takes precedence over channel priority (default:
                 False). Note: This feature is in beta and may change in a future
                 release.
   
          <B>--show-channel-urls</B>
                 Show channel urls (default: None).
   
          <B>--no-show-channel-urls</B>
                 Don't show channel urls.
   
          <B>--json</B> Report all output as json. Suitable for using conda programmati-
                 cally.
   
          <B>--debug</B>
                 Show debug output.
   
          <B>--verbose</B>, <B>-v</B>
                 Use once for info, twice for debug, three times for trace.
   
   
   </PRE>
   <H2>EXAMPLES</H2><PRE>
                 conda install -n myenv scipy
   
   
   
   
   </PRE>
   <H2>Anaconda, Inc.                     12i 2017                           CONDA(1)</H2><PRE>
   </PRE>
