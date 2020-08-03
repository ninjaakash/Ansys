#Ansys











class Ansys():
    def __init__(self,velocity, density, viscocity, diameter,y_plus,type_of_flow="internal"):
        self.velocity=velocity
        self.density = density
        self.viscocity = viscocity
        self.diameter = diameter
        self.y_plus = y_plus
        self.type_of_flow = type_of_flow
    def Reynolds_number(self):
        return (self.density*self.velocity*self.diameter)/self.viscocity
    def Skin_Friction_Coefficient(self):
        if self.type_of_flow.lower()=="internal":
            return 0.079* self.Reynolds_number()**(-0.25)
        if self.type_of_flow.lower()=="external":
            return 0.058* self.Reynolds_number()**(-0.2)

    def Wall_Shear_Stress(self):
        return 0.5 * self.Skin_Friction_Coefficient() * self.density * self.velocity ** 2

    def First_Cell_Height(self):
        print("To Capture boundry select y+ less than 5 if you dont have to do anything to boundry phenomenon then select y+ greater than 30")
        return self.y_plus * self.viscocity / (self.density * self.Wall_Shear_Stress())
