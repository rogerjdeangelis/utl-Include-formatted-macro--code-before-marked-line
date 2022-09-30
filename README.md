# utl-Include-formatted-macro--code-before-marked-line
Include macro utl_submit_r64 formatted code before line XX in the 1980s SAS classic editor
    %let pgm=utl-Include-formatted-macro--code-before-marked-line;

    Problem: Include macro utl_submit_r64 formatted code before line XX in the 1980s SAS classic editor.


    github
    https://tinyurl.com/bdzxtx2r
    ithub
https://tinyurl.com/bdzxtx2r
https://github.com/rogerjdeangelis/utl-Include-formatted-macro--code-before-marked-line




    /*
     _                   _
    (_)_ __  _ __  _   _| |_
    | | `_ \| `_ \| | | | __|
    | | | | | |_) | |_| | |_
    |_|_| |_| .__/ \__,_|\__|
            |_|
    */

    If you are using the 1980's classic editor

    Problem (solution uses the 1980s SAS classic editor)

    Command ===>

    00070
    00071 %utl_submit_r64('iris[1:5,]');
    00 72

    /*           _               _
      ___  _   _| |_ _ __  _   _| |_
     / _ \| | | | __| `_ \| | | | __|
    | (_) | |_| | |_| |_) | |_| | |_
     \___/ \__,_|\__| .__/ \__,_|\__|
                    |_|
    */

    00012 %macro utl_submit_r64(
    00013       pgmx
    00014      ,return=N
    00015      ,resolve=N
    00016      )/des="Semi colon separated set of R commands - drop
    00017
    00018   %utlfkil(%sysfunc(pathname(work))/r_pgm.txt);
    00019
    00020   /* clear clipboard */
    00021   filename _clp clipbrd;
    00022   data _null_;
    00023     file _clp;
    00024     put " ";
    00025   run;quit;
    00026
    00027   * write the program to a temporary file;
    00028   filename r_pgm "%sysfunc(pathname(work))/r_pgm.txt" lre
    00029
    00030   data _null_;
    00031     length pgm $32756;
    00032     file r_pgm;
    00033     if substr(upcase("&resolve"),1,1)="Y" then do;
    00034         pgm=resolve(&pgmx);
    00035      end;
    00036     else do;
    00037         pgm=&pgmx;
    00038      end;
    00039     put pgm;
    00040     putlog pgm;
    00041   run;
    00042
    00043   %let __loc=%sysfunc(pathname(r_pgm));
    00044
    00045   * pipe file through R;
    00046   filename rut pipe "D:\r412\R\R-4.1.2\bin\R.exe --vanill
    00047   data _null_;
    00048     file print;
    00049     infile rut recfm=v lrecl=32756;
    00050     input;
    00051     put _infile_;
    00052     putlog _infile_;
    00053   run;
    00054
    00055   filename rut clear;
    00056   filename r_pgm clear;
    00057
    00058   * use the clipboard to create macro variable;
    00059   %if %upcase(%substr(&return.,1,1)) ne N %then %do;
    00060     filename clp clipbrd ;
    00061     data _null_;
    00062      infile clp;
    00063      input;
    00064      putlog "macro variable &return = " _infile_;
    00065      call symputx("&return.",_infile_,"G");
    00066     run;quit;
    00067   %end;
    00068
    00069 %mend utl_submit_r64;
    00070
    00071 %utl_submit_r64('iris[1:5,]');

    /*
     _ __  _ __ ___   ___ ___  ___ ___
    | `_ \| `__/ _ \ / __/ _ \/ __/ __|
    | |_) | | | (_) | (_|  __/\__ \__ \
    | .__/|_|  \___/ \___\___||___/___/
    |_|
    */

    1. Put a B in the 1980s classic editor prefix area before '%utl_submit_r64'
    2. Hilight utl_submit_r64
    3. Go to the command line(hit bome key) and paste text and  add '.sas'
    4. Insert inc before utl_submit_r64.sas and hit enter

    I A command macro may be able to do all four steps with a single function key, mouse action

      or commmand macro.
    Somthing like
       :B; find '%';mark;find '(' mark; store;home; paste; tf; ??  untested

    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
