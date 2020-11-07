# CarOwnerShip - Solidity
> ## Introduction

This Codes are made for Lecture of Blockchain Theory and Practice was held in Utretch Summer School of Netherlands.

Our team made the business model of Car Recode and also made the Blockchain System using Solidity programming language.
 
Now I will go on an explanation about the concept of the business model and special part of codes


> ## UML of Car Onwership

The Picture shown below is UML of our business Model.

There are 7 nodes(Buyer, Government, Dealer, Seller, Insurancer, Maintenance, Recycle). 

Each node can access Car(Object) specific function.

And Our team made the each Object and its function based on this diagram.


![structure](https://blogfiles.pstatic.net/MjAxOTEyMDZfMjkx/MDAxNTc1NTk5NTgzNTY0.igm6SFH5wVTSR0nFDmUPgrCcm9Ni3XQBISda_wx3sBog.0-pBV9ks0ULVIqkSW6RF8zlmQorQz2f39JweGm15Vo0g.JPEG.hdh988/UML.jpg?type=w2)


>## SwimLane Image of Car Onwership

This is the SwimLane Of Car Ownership process. 

The left part of the picture(looked like 5 SwimLane) represents the process of car ownership proceeded by each node.

The right part of the picture represents the On-blockchain Part.
Also, we put the two-sided-arrow-signal to explain what information is linked to the On-blockchain part and Off-blockchain part. 

![structure](https://blogfiles.pstatic.net/MjAxOTEyMDZfNTIg/MDAxNTc1NTk5OTMyMDky.AbVimgoe41-4ujT_Wj2J4C3mwpufeE7HD-CUT2C8Nbcg.Q8p8nWNVW2iYnDCwk0aL94_BUiNWCNlsAxtd0CY1dmcg.JPEG.hdh988/BPMN%28proposed_case%29.jpg?type=w2)

> ## Composition of CarOwnership
> 1. [carOwnership](README.md#carOwnership)
>
> 2. [carTransantionBC](README.md#carTransantionBC)
  
<br/>  
  
>> ### **carOwnership** 


```java

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
<br/>

>> ### CarTransantionBC


```java

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
    
    mapping(uint => transanctionRecord) trans; //  **craete constructor by mapping**
    
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
