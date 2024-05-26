**In some cases you'll encounter errors like (cannot create efi system partition. error: 0x000036b7) (Cannot find room for the EFI system partition.)**

To fix this simply disable the windows recovery partition and then delete it

```
**DISABLE WINRE**
reagentc /disable

**USE DISKPART** //replace # with correct number based on your system
list disk    //select you harddrive/ssd
list partition #   //find the one partition that named system reserved or the one with 500mb+ size
select partition #   //select the one partition named system reserved or the one with 500mb+ size
delete partition override   //deletes the partition
```

