# Toolbox Utils

Should I include these?... will have to think about it 
## Chainable interface


## Resource survey, packaging, inspection
* Cross-toolpkglibbox identification of similar functionality
    * benchmarking comparison
    * cost analysis
    * abstracted package procurement

## function call syntax inspection
* cache function calls and execution profile
    * input/output sizes, types
    * input/output variable names
    * input/output parameter values
    * performance-profile
    * device and environment props
* 'mocking' to determine usage
    * 

## Builtin/undoc exposure
* for use with System objects
    * matlab.system.SystemProp.___
        * set/getParentGraph
        * setInstanceName
        * getInputNames
        * getSystemObjectDescriptionFromH1Line
        * sysObjNodeCloneHelper
        * [majorV, minorV] = getVersionNumber
        * getVersionString
        * showSimulateUsing
        * getPropertyGroups
    * matlab.system.SystemImpl.___
        * getExecutionSematicsImpl
        * [flag, sysmex] = isAccelerated(obj)
        * profileInfo = getProfileData()
        * getCachedInputSize
        * getAlternateBlock
* mshow
    * lists packages and package contents