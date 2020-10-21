**O TheOne.sol**
Ecrivez un contrat TheOne. Ce contrat devra posséder une fonction one qui retournera le nombre 1 lorsqu'elle sera appelée.

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.6.6;

contract TheOne {
    function one() public pure returns (uint256){
      return (1) ;
    }
}
```
**1 HelloWorld.sol**
Ecrivez un contrat HelloWorld.
Ce contrat devra posséder une fonction hello qui retournera la string "Hello world!" lorsqu'elle sera appelée.

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.6.6;

contract HelloWorld {
    function hello() public pure returns (string memory){
        return ("Hello World !");
    }
}
```

**2 SimpleStorage.sol
Ecrivez un contrat SimpleStorage qui modifiera/affichera le contenu d'une variable uint256 private storedData.
Une fonction get() retournera la valeur de storedData; Une fonction set(uint256 value) modifiera la valeur de storedData par value passé en paramètre. 

```
//SPDX-License-Identifier: MIT
pragma solidity ^0.6.0;

contract SimpleStorage {
    uint storedData;
    
    
function set(uint _value) public{
    storedData = _value;
}

function get() public view returns (uint256)
{
    return storedData;
}
}
```
**3 CheckOdd.sol**
Ecrivez un contrat CheckOdd. Ce contrat devra posséder une fonction check qui prendra en paramètre un uint et qui retournera true si le nombre passé en paramètre à checkest impair sinon elle retournera false.
```
//SPDX-License-Identifier: MIT
pragma solidity ^0.6.0;

contract CheckOdd{
    function check(uint256 _odd) public pure returns (bool){
        return _odd % 2 == 1 ? true : false ;
    }
}
```
**4 mapToMap.sol**
Ecrivez un contrat mapToMap. Ce contrat possédera une variable d'état earth public qui sera un mapping de string (des continents) vers un mapping de string (des pays de ce continent) vers une string (la capitale de ce pays); Renseigner directement dans le constructeur certaines valeurs comme:
```
earth["europe"]["france"] = "paris";
earth["amerique du sud"]["argentine"] = "buenos aires"
```
Ainsi pour récupérer la capitale de la France nous pourrions directement y avoir accès via remix en passant "europe" et "france" en paramètres.

```
//SPDX-License-Identifier: MIT
pragma solidity ^0.6.0;

contract mapToMap {
    mapping(string => mapping(string => string)) private earth;

    constructor() public{
        earth["Europe"]["France"]="Paris";
        earth["Amerique du Sud"]["Argentine"]="Buenos-Aires";
    }
    function map(string memory _continent, string memory _country)public view returns (string memory){
        return earth[_continent][_country];
    }
}
```
**5 Contact.sol**
Ecrivez un contrat Contact qui permettra d'enregistrer ou de récupérer des info sur un contact en fonction de son adresse Ethereum. Les informations pour chaque contact seront stockées dans une struct avec les champs suivants: string name, string email, string phone.
Un mapping nous donnera la correspondance entre 1 adresse Ethereum et ces informations.
Une fonction addContact nous permettra d'ajouter un nouveau contact avec l'adresse Ethereum, le nom, l'email et le téléphone du contact en arguments à cette fonction.
Une fonction getContact(address _addr) nous permettra de récupérer les informations d'un contact en fonction d'une addresse Ethereum. Pour que la fonction getContact(address _addr) fonctionne il faudra ajouter pragma experimental ABIEncoderV2; comme directive de pragma.

```
//SPDX-License-Identifier: MIT
pragma solidity ^0.6.0;
pragma experimental ABIEncoderV2;

contract Contact {
    struct InfosContact {
        string name;
        string email;
        string phone;
    }

mapping(address => InfosContact) public infos;

function addContact(
    address _addr,
    string memory _name,
    string memory _email,
    string memory _phone)
    public{
        infos[_addr] = InfosContact(_name,_email,_phone);
    }
    function getContact(address _addr) public view returns (InfosContact memory){
        return infos[_addr];
    }
}
