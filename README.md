#include <stdio.h>
#include <math.h>
#include <stdlib.h>

#define PI 3.141592653589793

int main(void) {
    double wavelength;  
    double a1, a2, a3; 
    double angle1, angle2, angle3;
    int m;              

    printf("=== Problem #1: Which Slit Bent the Light Most? ===\n");

    
    printf("Enter the wavelength (in nm): ");
    scanf("%lf", &wavelength);

    
    if (wavelength < 300.0 || wavelength > 800.0) {
        printf("Out of range (300-800 nm). Exiting.\n");
        return 1; 
    }

    
    printf("Enter the diffraction order m (e.g., 1): ");
    scanf("%d", &m);

    
    printf("Enter slit width a1 (in nm): ");
    scanf("%lf", &a1);
    printf("Enter slit width a2 (in nm): ");
    scanf("%lf", &a2);
    printf("Enter slit width a3 (in nm): ");
    scanf("%lf", &a3);

    
   
    angle1 = asin((m * wavelength) / a1);
    angle2 = asin((m * wavelength) / a2);
    angle3 = asin((m * wavelength) / a3);

    
    angle1 = angle1 * 180.0 / PI;
    angle2 = angle2 * 180.0 / PI;
    angle3 = angle3 * 180.0 / PI;

    
    double maxAngle = angle1;
    int maxIndex = 1;

    if (angle2 > maxAngle) {
        maxAngle = angle2;
        maxIndex = 2;
    }
    if (angle3 > maxAngle) {
        maxAngle = angle3;
        maxIndex = 3;
    }

    
    printf("\n--- Results ---\n");
    printf("Angle for slit #1 = %.4f degrees\n", angle1);
    printf("Angle for slit #2 = %.4f degrees\n", angle2);
    printf("Angle for slit #3 = %.4f degrees\n", angle3);
    printf("Slit #%d bends the light the most (largest angle).\n", maxIndex);

    return 0;
}
