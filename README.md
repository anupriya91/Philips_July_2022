# Philips_July_2022

Design patterns training assignments

Assignment - 1 
//Swift Code
/*
func batteryIsOk(temperature: Float, soc: Float, chargeRate: Float) {
  if(temperature < 0 || temperature > 45) {
    cout << "Temperature out of range!\n";
    return false;
  } else if(soc < 20 || soc > 80) {
    cout << "State of Charge out of range!\n";
    return false;
  } else if(chargeRate > 0.8) {
    cout << "Charge Rate out of range!\n";
    return false;
  }
  return true;
}
*/
Findings: The code is violating Single Responsibility Principle on the following points:

The method has 3 responsiblites: temperature, soc, chargeRate
Validation loic for any one of the above changes will result in a change in the method
Individual ifs which are testing for 2 conditions are not violation of SRP in themselves as they deal with the same parameter

class Battery {
    var temperature: Float
    var soc: Float
    var chargeRate: Float
}

extension Battery {
    func isTemperatureOutOfRange() -> Bool {
        return (temperature < 0 || temperature > 45) ? true : false
    }
    
    func isSocOutOfRange() -> Bool {
        return (soc < 20 || soc > 80) ? true : false
    }
    
    func isChargeRateOutOfRange() -> Bool {
        return (chargeRate > 0.8) ? true : false
    }
}

func batteryIsOk(temperature: Float, soc: Float, chargeRate: Float) {
    return (isTemperatureOutOfRange() || isSocOutOfRange() || isChargeRateOutOfRange()) ? false : true
}
