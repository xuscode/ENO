<!--
 * @Name: 
 * @Data: YYYY-MM-DD HH:mm:ss
 * @Input: 
-->

# CATBatchStarter

=== "english"

    PS C:\Program Files\Dassault Systemes\B423\win_b64\code\bin> .\CATBatchStarter.exe
    CATBatchStarter requires at least one argument

    usage : CATBatchStarter -input parametersfile [-host hostname] [-driver drivername] [-allow_visu]
                            [-output path] [-verbose]  [-u][-h][-?]

    arguments :
    -u / -h / -? : arguments help
    -input parametersfile : fullpath of the batch xml parameter file.
    -host <hostname> : where hostname is the name of the remote machine,
                        resquest a remote execution
    -allow_visu : to allow the batch to access the graphical adapter (if any),
                    otherwise batch which need one will exit with RC = 7
    -output <path> : where path is the fullpath of a file or a directory
        where to put the execution log of the batch
    -verbose : activates the execution traces
    -driver <drivername> : where drivername is BB(backbone)
        or MQ(MQSeries), default is BB
    PS C:\Program Files\Dassault Systemes\B423\win_b64\code\bin>


=== "chinese"

    PS C:\Program Files\Dassault Systemes\B423\win_b64\code\bin> .\CATBatchStarter.exe
    CATBatchStarter requires at least one argument

    usage : CATBatchStarter -input parametersfile [-host hostname] [-driver drivername] [-allow_visu]
                            [-output path] [-verbose]  [-u][-h][-?]

    arguments :
    -u / -h / -? : arguments help
    -input parametersfile : fullpath of the batch xml parameter file.
    -host <hostname> : where hostname is the name of the remote machine,
                        resquest a remote execution
    -allow_visu : to allow the batch to access the graphical adapter (if any),
                    otherwise batch which need one will exit with RC = 7
    -output <path> : where path is the fullpath of a file or a directory
        where to put the execution log of the batch
    -verbose : activates the execution traces
    -driver <drivername> : where drivername is BB(backbone)
        or MQ(MQSeries), default is BB
    PS C:\Program Files\Dassault Systemes\B423\win_b64\code\bin>

