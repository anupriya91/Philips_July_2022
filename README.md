# Philips_July_2022

Design patterns training assignments

Assignment - 1 //C++ Code bool batteryIsOk(float temperature, float soc, float chargeRate) { if(temperature < 0 || temperature > 45) { cout << "Temperature out of range!\n"; return false; } else if(soc < 20 || soc > 80) { cout << "State of Charge out of range!\n"; return false; } else if(chargeRate > 0.8) { cout << "Charge Rate out of range!\n"; return false; } return true; }

Findings: The code is violating Single Responsibility Principle on the following points:

The method has 3 responsiblites: temperature, soc, chargeRate
Validation loic for any one of the above changes will result in a change in the method
Individual ifs which are testing for 2 conditions are not violation of SRP in themselves as they deal with the same parameter
