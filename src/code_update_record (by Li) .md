# NHWAVE Update Records

---  
**Author**: Zhisong Li
**Email**:  lizhisong@sjtu.edu.cn, lizhisong@alunami.sjtu.edu.cn, lizhisongsjtu@163.com

**Forked from `https://github.com/NHWAVE/NHWAVE`**

---
## UPDATE_0001

**Date**: 2025/12/22

**Description**  

- [x] Add Grimshaw solitary from the left boundary
- [x] Add Grimshaw solitary from the internal mass source
- [ ] Add Fenton solitary from the internal mass source


---
## UPDATE_0002

**Date**: 2025/12/22

**Description**  

- [x] Add new functions: nhwave could read parameters from arbitary input.txt file.
- [x] Add new functions: file name of water depth can be read from input.txt file by default.
- [x] Add new functions: file name of initial eta0 can be read from input.txt file by default.
- [x] Add new functions: file name of initial u0 can be read from input.txt file by default.
- [x] Add new functions: file name of initial v0 can be read from input.txt file by default.
- [x] Add new functions: file name of initial w0 can be read from input.txt file by default.
- [x] Add new functions: file name of initial s0 can be read from input.txt file by default.

---
## UPDATE_0003

**Date**: 2025/12/22

**Description**  

- [x] Add new functions: nhwave could read parameters from arbitary input.txt file.

- [x] add the variable `INPUT_NAME` in the subroutine `read_input`.
  - This modification draws on the approach used in **Funwave-TVD**.

  ```fortran
    ! >by Zhisong Li, based on Funwave-TVD.
     character(len=80) :: INPUT_NAME 

     ! read from input.txt
     FILE_NAME='input.txt'
     ! read everything from input.txt

      !>by Zhisong Li
      !> Get the argument from the command.
      !> If no input in command, file name is 'input.txt' (same as before)
      !> If the input comes with other name, read the correponding file
      CALL GETARG(1,INPUT_NAME) 
      if (INPUT_NAME .eq. '') Then
        FILE_NAME='input.txt'
      Else
        FILE_NAME=INPUT_NAME
      endif
  ```


---
## UPDATE_0004

**Date**: 2025/12/13

**Description**  

- [x] This update comes from https://github.com/MartinHu1997/NHWAVE
- [x] Debug (Vegetation Model)
  - Replace the variable 'Vegbv' with 'StemD' at two places (in the subroutine kepsilon_3D of nhwave.F)  

  - 'Vegbv' represents the Stem Size and was no longer used now.  

  - 'StemD' represents the Stem Size  

- [x] The local variables, 'cfk' and 'cfe', are no longer defined in the subroutines kepsilon and kepsilon_3D now (nhwave.F)  
  - 'Cfk' and 'Cfe' are required for input file now (input.txt)  