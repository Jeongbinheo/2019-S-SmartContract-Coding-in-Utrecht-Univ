# CarOwnerShip - Solidity
> ## Introduction
> 




> ## UML of Car Onwership
> 


>## SwimLane Image of Car Onwership
>


> ## Composition of CarOwnership
> 1. [carOwnership](README.md#carOwnership)
>
> 2. [carRecordBC](README.md#carRecordBC)
>
> 3. [carAccidentBC](README.md#carAccidentBC)
>
> 4. [carRentalBC](README.md#carRentalBC)
>
> 5. [carRepairBC](README.md#carRepairBC)
>
>6. [carTransantionBC](README.md#carTransantionBC)
  
  ### **carOwnership** 

```
pragma solidity ^0.4.12;

contract CarOwnership {

    struct CarMasterInfo {
       
       CarRecord carRecord;
       repairRecord [] repairRecords;
       accidentRecord [] accidentRecords;
       transanctionRecord [] transanctionRecords;
       rentalRecord [] rentalRecords;
    }
    
    
    struct CarRecord
    {
        string dateOfMainterancet;
        string originOfMainternace;
        string vin;
        string model;
        string make;
        int numCyclinders;
        int numEngine;
        int mileage;
    }

    struct repairRecord
    {
        string dateRepaired;
        string timeRepaired;
        string service;
    }
    
    struct accidentRecord
    {
        string dateAccident;
        string timeAccident;
        string description;
    }
    
    struct transanctionRecord
    {
        string dateTransanction;
        string amount;
        string buyerDesc;
        string sellerDesc;
    }
    
    struct rentalRecord
    {
        string dateRental;
        int rentalDays;
        string rentToDesc;
        string rentByDesc;
        
    }

    function setCarRecord(string _dateOfMainterancet,
        string _originOfMainternace,
        string _vin,
        string _model,
        string _make,
        int _numCyclinders,
        int _numEngine,
        int _mileage)
    {
        dateOfMainterancet = _dateOfMainterancet;
        originOfMainternace = ;
        string vin;
        string model;
        string make;
        int numCyclinders;
        int numEngine;
        int mileage;
    }
}

```
 ### **carRecordBC**
 ```
pragma solidity ^0.4.12;

contract CarRecordBC {

    uint public currentBalance;

    struct CarRecord
    {
        int registrationNum;
        string dateOfManufacture;
        string originOfManufacture;
        string vin;
        string model;
        string make;
        int numCyclinders;
        int numEngine;
        int mileage;
    }
    CarRecord carRecord;
    int numRegistrationNum;
    address public myaddress =0x068eF6F367c6E54266A14041dCE460D5A62dDb3e;
    address public governmentAddress=0x43EFa709c7f973667232dEFf99F79D5399cd8aAA;
    
    function CarRecordBC() public
    {
        numRegistrationNum = 0;
        
        currentBalance=0;
        
    }
    
   function depositTokken()public payable
    {// deposit` tokken function

    }    
    
    function withdraw() public
    {
        myaddress.transfer(address(this).balance);
    }
    
    function getBallance() public
    {
        currentBalance  = address(this).balance;
    }
    

    
    function awardToken(uint amount) public 
    {
        governmentAddress.transfer(amount);

    }
    
    function generateRegisterNum() public returns (int)
    {
        numRegistrationNum = numRegistrationNum + 1;
    }
    
     function setCarRecord( 
        
        
        string _dateOfManufacture,
        string _originOfManufacture,
        string _vin,
        string _model,
        string _make,
        int _numCyclinders,
        int _numEngine,
        int _mileage)
    {
        carRecord.registrationNum = generateRegisterNum();
        carRecord.dateOfManufacture = _dateOfManufacture;
        carRecord.originOfManufacture = _originOfManufacture;
        carRecord.vin = _vin;
        carRecord.model = _model;
        carRecord.make = _make;
        carRecord.numCyclinders = _numCyclinders;
        carRecord.numEngine = _numEngine;
        carRecord.mileage = _mileage;
        
        awardToken(10);
    }
    
    function getRegistrationNum() public returns (int)
    {
        return carRecord.registrationNum;        
    }
    function getCarRecordDFM() public returns (string)
    {
        return carRecord.dateOfManufacture;        
    }
    
    function getCarRecordOFM() public returns (string)
    {
        return carRecord.originOfManufacture;        
    }
    
    function getCarRecordVIN() public returns (string)
    {
        return carRecord.vin;        
    }
    
    function getCarRecordModel() public returns (string)
    {
        return carRecord.model;        
    }
    
    function getCarRecordMake() public returns (string)
    {
        return carRecord.make;        
    }
    
    function getCarRecordNumCylinders() public returns (int)
    {
        return carRecord.numCyclinders;        
    }
    
    function getCarRecordNumEngine() public returns (int)
    {
        return carRecord.numEngine;        
    }
    
    function getCarRecordMileage() public returns (int)
    {
        return carRecord.mileage;        
    }
    
}
 
 ```
  
 ### **carAccidentBC**
 ```
pragma solidity ^0.4.12;


contract CarAccidentBC {

    uint public currentBalance;
    
    struct AccidentRecord
    {
        string dateAccident;
        string timeAccident;
        string description;
    }
    
    int numAccidentRecords;
    address public myaddress =0x068eF6F367c6E54266A14041dCE460D5A62dDb3e;
    address public insuranceAddress=0x43EFa709c7f973667232dEFf99F79D5399cd8aAA;
  
    mapping (int => AccidentRecord) accidentRecords;
    
    function CarAccidentBC() public
    {
        numAccidentRecords = 0;
        currentBalance=0;
        
    }
    
    function depositTokken()public payable
    {// deposit` tokken function

    }    
    
    function withdraw() public
    {
        myaddress.transfer(address(this).balance);
    }
    
    function getBallance() public
    {
        currentBalance  = address(this).balance;
    }
    
    function awardToken(uint amount) public 
    {
        insuranceAddress.transfer(amount);

    }

    
    function strAppend(string s1, string s2) public returns (string) 
    {
        bytes newString;
        
        bytes memory str1b = bytes(s1);
        bytes memory str2b = bytes(s2);
        
        uint str1l=bytes(s1).length;
        uint str2l=bytes(s2).length;
        uint a =0;
        uint b=0;
        for(uint i=0; i< (str1l+str2l); i++)
        {
            
            if(a<str1l)
            {
                newString[i]=str1b[a];
                a=a+1;
                
            }
            else
            {
                newString[i]=str2b[b];
                b=b+1;
            }
            
        }
        return string(newString);
    }
    
    function setAccidentRecord(string _dateAccident,
        string _timeAccident,
        string _description) public
    {
       
        accidentRecords[numAccidentRecords].dateAccident = _dateAccident;
        accidentRecords[numAccidentRecords].timeAccident = _timeAccident;
        accidentRecords[numAccidentRecords].description = _description;
        numAccidentRecords = numAccidentRecords + 1;
        
        
         awardToken(10);
    }
    
    
    function getDateAccident() public returns (string)
    {
        string ret;
        for(int i= 0; i< numAccidentRecords; i++)
        {
            
            strAppend(ret,
            accidentRecords[numAccidentRecords].dateAccident);
            strAppend(ret,", ");
            
            strAppend(ret,
             accidentRecords[numAccidentRecords].timeAccident);
            strAppend(ret,", ");
            
            strAppend(ret, accidentRecords[numAccidentRecords].description);
            strAppend(ret,", ");
        }   
        return ret;
    }
}
```

### **carRentalBC**
```
pragma solidity ^0.4.17;

contract CarRentalBC 
{
    uint256 public currentBalance;
    uint private rentalCount;//count how many repair?
 
    address public myaddress =0x068eF6F367c6E54266A14041dCE460D5A62dDb3e;
    address rentalCompanyWallet=0x43EFa709c7f973667232dEFf99F79D5399cd8aAA;
    
    function awardTokken(uint amount ) public // award tokken function
    {
        rentalCompanyWallet.transfer(amount);
    }
    
    function depositTokken()public payable
    {//deposit tokken function

    }    
    
    function withdraw() public
    {
        myaddress.transfer(address(this).balance);
    }
    
    function getBallance() public view returns (uint256)
    {
        return address(this).balance;
    }
 
    function concenString(string str1,string str2) public returns (string)
    {
        bytes memory newString;
        
        bytes memory str1b = bytes(str1);
        bytes memory str2b = bytes(str2);
        
        uint str1l=bytes(str1).length;
        uint str2l=bytes(str2).length;
        
        uint a = 0;
        uint b = 0;
        
        for(uint i=0; i< (str1l+str2l); i++)
        {
            if(a<str1l)
            {
                newString[i]=str1b[a] ;
                a=a+1;   
            }else
            {
                newString[i]=str2b[b];
                b=b+1;
            }
        }
        return string(newString);
    }
    
    struct rentalRecord
    {
        string dateRental;
        string rentalDays;
        string rentToDesc;
        string rentByDesc;
    }
    
    mapping(uint => rentalRecord) ren; // craete constructor by mapping
    
    function setRentalRecord(
        string _dateRental,
        string _rentalDays,
        string _rentToDesc,
        string _rentByDesc)
    {
        ren[rentalCount].dateRental = _dateRental; //linked the constructor
        ren[rentalCount].rentalDays = _rentalDays;
        ren[rentalCount].rentToDesc = _rentToDesc;
        ren[rentalCount].rentByDesc =_rentByDesc;
        
        addRentalCount();
        
        awardTokken(1000000000000000000); // input information, give tokken 1eher
    }
    

    // individual print
    function getDataRental() public returns (string)
    {
         string memory str;
        
        for(uint i=0; i<rentalCount; i++)
        {

            concenString(str,ren[rentalCount].dateRental);
            concenString(str,",");
            
            concenString(str,ren[rentalCount].rentalDays);
            concenString(str,",");
            
            concenString(str, ren[rentalCount].rentToDesc);
            concenString(str,",");
            
            concenString(str,ren[rentalCount].rentByDesc);
            concenString(str,",");
            
            return str;
        }
    }
    

    
     function CarRentalBC () public
    {
        rentalCount=0;
        currentBalance=0;

    }
    
    function addRentalCount() public
    {
        rentalCount++;
    }
    
    function getRentalCount() public returns (uint)
    {
        return rentalCount;
    }
  
    
}
```
### **carRepairBC**
```
pragma solidity ^0.4.12;

contract CarRepairBC
{
    uint public currentBalance;
    uint private repairCount;//count how many repair?
    
    address public myaddress =0x068eF6F367c6E54266A14041dCE460D5A62dDb3e;
    address public mainTainence=0x43EFa709c7f973667232dEFf99F79D5399cd8aAA;

    function awardTokken(uint amount ) public // award tokken function
    {
        mainTainence.transfer(amount);
    }
    
    function depositTokken()public payable
    {// deposit` tokken function

    }    
    
    function withdraw() public
    {
        myaddress.transfer(address(this).balance);
    }
    
    function getBallance() public
    {
        currentBalance  = address(this).balance;
    }

    function concenString(string str1,string str2) public returns (string)
    {
        
        bytes memory newString;
        
        bytes memory str1b = bytes(str1);
        bytes memory str2b = bytes(str2);
        
        uint str1l=bytes(str1).length;
        uint str2l=bytes(str2).length;
        
        uint a = 0;
        uint b = 0;
        
        for(uint i=0; i< (str1l+str2l); i++)
        {
            
            if(a<str1l)
            {
                newString[i]=str1b[a] ;
                a=a+1;
                
            }else
            {
                newString[i]=str2b[b];
                b=b+1;
            }
            
        }
        
        return string(newString);
    }
    
    struct repairRecord
    {
        string dateRepaired;
        string timeRepaired;
        string service;
    }
    
    mapping(uint => repairRecord) rep; // craete constructor by mapping

    
    function setRepairRecord(
        string _dateRepaired,
        string _timeRepaired,
        string _service)
    {

        
        rep[repairCount].dateRepaired = _dateRepaired; //linked the constructor
        rep[repairCount].timeRepaired = _timeRepaired;
        rep[repairCount].service = _service;
        
      
        addRepairCount();// add count
        
        awardTokken(1000000); // input information, give tokken 100000
    }
    

    // individual print
    function getDataRepaired() public returns (string)
    {
        string memory str;
        
        for(uint i=0; i<repairCount; i++)
        {

            
            concenString(str,rep[repairCount].dateRepaired);
            concenString(str,",");
            
            concenString(str,rep[repairCount].timeRepaired);
            concenString(str,",");
            
            concenString(str,rep[repairCount].service);
            concenString(str,",");
            
            return str;
        }
    }
    

     function CarRepairBC() public
    {
        repairCount=0;
        currentBalance=0;
    }
    
    function addRepairCount() public
    {
        repairCount++;
    }
    
    function getRepairCount() public returns (uint)
    {
        return repairCount;
    }
    
}
```
### **carTransantionBC**
```
pragma solidity ^0.4.12;

contract CarTransanctionBC 
{
    uint public currentBalance;
    uint private transanctionCount;//count how many repair?
    
    address public myaddress =0x068eF6F367c6E54266A14041dCE460D5A62dDb3e;
    address public seller=0x43EFa709c7f973667232dEFf99F79D5399cd8aAA;

    function awardTokken(uint amount ) public // award tokken function
    {
        seller.transfer(amount);
    }
    
    function depositTokken()public payable
    {// deposit` tokken function

    }    
    
    function withdraw() public
    {
        myaddress.transfer(address(this).balance);
    }
    
    function getBallance() public
    {
        currentBalance  = address(this).balance;
    }
    

    function concenString(string str1,string str2) public returns (string)
    {
        
        bytes memory newString;
        
        bytes memory str1b = bytes(str1);
        bytes memory str2b = bytes(str2);
        
        uint str1l=bytes(str1).length;
        uint str2l=bytes(str2).length;
        
        uint a = 0;
        uint b = 0;
        
        for(uint i=0; i< (str1l+str2l); i++)
        {
            
            if(a<str1l)
            {
                newString[i]=str1b[a] ;
                a=a+1;
                
            }else
            {
                newString[i]=str2b[b];
                b=b+1;
            }
            
        }
        
        return string(newString);
    }
    
    struct transanctionRecord
    {
        string dateTransanction;
        string amount;
        string buyerDesc;
        string sellerDesc;
    }
    
    mapping(uint => transanctionRecord) trans; // craete constructor by mapping
    
    function setTransanctionRecord(
        string _dateTransanction,
        string _amount,
        string _buyerDesc,
        string _sellerDesc)
    {
        trans[transanctionCount].dateTransanction = _dateTransanction; //linked the constructor
        trans[transanctionCount].amount = _amount;
        trans[transanctionCount].buyerDesc = _buyerDesc;
        trans[transanctionCount].sellerDesc = _sellerDesc;
        
        addTransanctionCount();
        
        awardTokken(10); // input information, give tokken 10
    }
    

    // individual print
    function getDataTransanction() public returns (string)
    {
        string memory str;
        
        for(uint i=0; i<transanctionCount; i++)
        {

            concenString(str,trans[transanctionCount].dateTransanction);
            concenString(str,",");
            
            concenString(str,trans[transanctionCount].amount);
            concenString(str,",");
            
            concenString(str,trans[transanctionCount].buyerDesc);
            concenString(str,",");
            
            concenString(str,trans[transanctionCount].sellerDesc);
            concenString(str,",");
            
            return str;
        }
    }
    
    
     function CarTransanctionBC() public
    {
        transanctionCount=0;
        currentBalance=0;
        
    }
    
    function addTransanctionCount() public
    {
        transanctionCount++;
    }
    
    function getTransanctionCount() public returns (uint)
    {
        return transanctionCount;
    }  
    
}

```
