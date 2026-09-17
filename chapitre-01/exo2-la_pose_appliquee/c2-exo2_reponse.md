    #include <iostream>
    #include <iomanip>
    using namespace std;
    
    struct Vecteur3 {
        double x;
        double y;
        double z;
    };
    
    struct Quaternion {
        double w;
        double x;
        double y;
        double z;
    };
    
    struct Pose {
        Vecteur3 position;
        Quaternion rotation;
    };
    
    // Applique une pose à un point : rotation puis translation
    Vecteur3 appliquerPose(const Pose& pose, const Vecteur3& point) {
        double w = pose.rotation.w;
        double x = pose.rotation.x;
        double y = pose.rotation.y;
        double z = pose.rotation.z;
    
    // Rotation du point par le quaternion normalisé
    double ix =  w * point.x + y * point.z - z * point.y;
    double iy =  w * point.y + z * point.x - x * point.z;
    double iz =  w * point.z + x * point.y - y * point.x;
    double iw = -x * point.x - y * point.y - z * point.z;

    double rx = ix * w + iw * -x + iy * -z - iz * -y;
    double ry = iy * w + iw * -y + iz * -x - ix * -z;
    double rz = iz * w + iw * -z + ix * -y - iy * -x;

    // Translation après la rotation
    return {
        rx + pose.position.x,
        ry + pose.position.y,
        rz + pose.position.z
    };
    }
    
    int main() {
        Pose pose;
        Vecteur3 point;

    /*
       Lecture de la pose :
       position : px py pz
       quaternion : w x y z
       point : x y z
    */

    cin >> pose.position.x
        >> pose.position.y
        >> pose.position.z;

    cin >> pose.rotation.w
        >> pose.rotation.x
        >> pose.rotation.y
        >> pose.rotation.z;

    cin >> point.x
        >> point.y
        >> point.z;

    Vecteur3 resultat = appliquerPose(pose, point);

    cout << fixed << setprecision(4);
    cout << resultat.x << " "
         << resultat.y << " "
         << resultat.z << endl;

    return 0;
    }