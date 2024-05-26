**In some cases you'll encounter errors like (cannot create efi system partition. error: 0x000036b7) (Cannot find room for the EFI system partition.)**

To fix this simply disable the windows recovery partition and then delete it


**DISABLE WINRE**
```
reagentc /disable
```
**USE DISKPART**                    //replace # with correct number based on your system
```
list disk                          //select you harddrive/ssd
list partition #                  //find the one partition that named system reserved or the one with 500mb+ size
select partition #               //select the one partition named system reserved or the one with 500mb+ size
delete partition override       //deletes the partition
```


**Now convert using mbr2gpt**

REPLACE # with the correct disk number!!

```
mbr2gpt /validate /disk:# /allowfullos
mbr2gpt /convert /disk:# /allowfullos
```

Reboot and change bios settings to uefi    (secureboot or disable csm)

**NOW TO RECOVER THE WINDOWS RECOVERY!!**

go to disk management, see if there is some unallocated space left. if not create new one (SHRINK) 1024MB
go to diskpart and select the newly created partition, and use comman 
``
set id=de94bba4-06d1-4d40-a16a-bfd50179d6ac
``

now launch admin cmd and re-enable recovery using command reagentc /enable 

check if enabled 
``
reagentc /info
``

**THAT's IT** 
