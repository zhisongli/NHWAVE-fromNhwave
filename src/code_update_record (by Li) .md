
# `NHWAVE-fromNhwave` Update Records

---
## 1. Information of this repository

| Column A       | Column B                  |
|------------------|---------------------------------------------|
| Author       | **Dr. Zhisong Li**           |
| Email        | lizhisong@sjtu.edu.cn, lizhisongsjtu@163.com |
| Original repository  | `https://github.com/NHWAVE/NHWAVE`     |
| Current repository  | `https://github.com/zhisongli/NHWAVE-fromNhwave`     |

---
## 2. Development team members

| Name             | GitHub Username   | Email                | Affiliation              | Role         |
|------------------|-------------------|----------------------|--------------------------|--------------|
| Jim Kirby        | JimKirby          | kirby@udel.edu       | University of Delaware   | Group owner  |
| Gangfeng Ma      | gangfengma        | gma@odu.edu          | Old Dominion University  |              |
| Fengyan Shi      | fengyanshi        | fyshi@udel.edu       | University of Delaware   |              |
| Morteza Derakhti | derakhti          | derakhti@uw.edu      | University of Washington |              |
| Cheng Zhang      | chzhangudel       | chzhang@udel.edu     | University of Delaware   |              |
| Martin Hu | MartinHu1997 |  hulihan@hhu.edu.cn | Hohai University |


---

## 3. Update history

### 3.1 UPDATE_0001
**Date**: 2025/12/22  
**Description**  
- [x] Added Grimshaw solitary wave generation from the left boundary  
- [x] Added Grimshaw solitary wave generation from the internal mass source  
- [ ] Added Fenton solitary wave generation from the internal mass source (in progress)  

---
### 3.2 UPDATE_0002
**Date**: 2025/12/22  
**Description**  
- [x] Added new functionality: NHWAVE can now read parameters from an arbitrary `input.txt` file  
- [x] Added new functionality: The filename for water depth can now be specified in `input.txt` by default  
- [x] Added new functionality: The filename for initial eta (`eta0`) can now be specified in `input.txt` by default  
- [x] Added new functionality: The filename for initial u-velocity (`u0`) can now be specified in `input.txt` by default  
- [x] Added new functionality: The filename for initial v-velocity (`v0`) can now be specified in `input.txt` by default  
- [x] Added new functionality: The filename for initial w-velocity (`w0`) can now be specified in `input.txt` by default  
- [x] Added new functionality: The filename for initial sediment concentration (`s0`) can now be specified in `input.txt` by default  

---
### 3.3 UPDATE_0003
**Date**: 2025/12/22  
**Description**  
- [x] Added new functionality: NHWAVE can now read parameters from an arbitrary input file  
- [x] Introduced the variable `INPUT_NAME` in the subroutine `read_input`  
- This modification is inspired by the approach used in **Funwave-TVD**  

  ```fortran
    ! >by Zhisong Li, based on Funwave-TVD.
     character(len=80) :: INPUT_NAME
     ! read from input.txt
     FILE_NAME='input.txt'
     ! read everything from input.txt
      !>by Zhisong Li
      !> Get the argument from the command line.
      !> If no argument is provided, the filename defaults to 'input.txt' (as before)
      !> If a different filename is provided, the corresponding file will be read
      CALL GETARG(1,INPUT_NAME)
      if (INPUT_NAME .eq. '') Then
        FILE_NAME='input.txt'
      Else
        FILE_NAME=INPUT_NAME
      endif
  ```

---
### 3.4 UPDATE_0004
**Date**: 2025/12/13  
**Description**  
- [x] This update is derived from https://github.com/MartinHu1997/NHWAVE  
- [x] Debugged the vegetation model  
- Replaced the variable `Vegbv` with `StemD` in two locations (in the subroutine `kepsilon_3D` of `nhwave.F`)  
- `Vegbv` previously represented stem size but is no longer used  
- `StemD` now represents stem diameter  
- [x] Removed local variables 'cfk' and 'cfe' from the subroutines `kepsilon` and `kepsilon_3D` in `nhwave.F`  
- `Cfk` and `Cfe` are now required as input parameters in `input.txt`