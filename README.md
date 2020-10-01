import android.content.pm.PackageManager;
import android.graphics.Bitmap;
import android.hardware.Camera ;
import android.os.Bundle;
import android.provider.MediaStore;
import android.view.View;
import android.widget.Button;
import android.widget.ImageView;

public class MainActivity extends AppCompatActivity {
    private Button takePictureButton;
    private ImageView imageView;
    private String TAG;
    //private Object Context;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        getSupportActionBar().hide();
        setContentView(R.layout.activity_main);
        takePictureButton = (Button) findViewById(R.id.button_image);
        imageView = (ImageView) findViewById(R.id.imageview);

        //if (ContextCompat.checkSelfPermission(this, Manifest.permission.CAMERA) != PackageManager.PERMISSION_GRANTED) {
        //takePictureButton.setEnabled(false);
        //ActivityCompat.requestPermissions(this, new String[] { Manifest.permission.CAMERA, Manifest.permission.WRITE_EXTERNAL_STORAGE }, 0);
        /** Check if this device has a camera */
        /** Check if this device has a camera */

    }

    private boolean checkCameraHardware(Context context) {
        if (context.getPackageManager().hasSystemFeature(PackageManager.FEATURE_CAMERA)) {
            // this device has a camera
            return true;
        } else {
            // no camera on this device
            return false;
        }
    }
    public static Camera getCameraInstance() {
       Camera c = null;
        try {
            c = Camera.open(); // attempt to get a Camera instance
        } catch (Exception e) {
            return c; // Camera is not available (in use or does not exist)
        }
        return c;
    }

    public void takePicture(View view) {
        Intent newCameraApp = new Intent(android.provider.MediaStore.ACTION_IMAGE_CAPTURE);
        startActivityForResult( newCameraApp, 1337);
        Intent camera_intent = new Intent(MediaStore.ACTION_IMAGE_CAPTURE);
        startActivityForResult(camera_intent, 123);
       ////// protected void onActivityResult(int requestCode, int resultCode, Intent data) { }
    }


    //return c; // returns null if camera is unavailable
        /**
         * A safe way to get an instance of the Camera object.
         */

        /** A basic Camera preview class */
        /*public class CameraPreview extends SurfaceView implements SurfaceHolder.Callback {
            private SurfaceHolder mHolder;
            private Camera mCamera;

            public CameraPreview(Context context, Camera camera) {
                super(context);
                mCamera = camera;

                // Install a SurfaceHolder.Callback so we get notified when the
                // underlying surface is created and destroyed.
                mHolder = getHolder();
                mHolder.addCallback(this);
                // deprecated setting, but required on Android versions prior to 3.0
                mHolder.setType(SurfaceHolder.SURFACE_TYPE_PUSH_BUFFERS);
            }

            public void surfaceCreated(SurfaceHolder holder) {
                // The Surface has been created, now tell the camera where to draw the preview.
                try {
                    mCamera.setPreviewDisplay(holder);
                    mCamera.startPreview();
                } catch (IOException e) {
                    Log.d(TAG, "Error setting camera preview: " + e.getMessage());
                }
            }

            public void surfaceDestroyed(SurfaceHolder holder) {
                // empty. Take care of releasing the Camera preview in your activity.
            }

            public void surfaceChanged(SurfaceHolder holder, int format, int w, int h) {
                // If your preview can change or rotate, take care of those events here.
                // Make sure to stop the preview before resizing or reformatting it.

                if (mHolder.getSurface() == null) {
                    // preview surface does not exist
                    return;
                }

                // stop preview before making changes
                try {
                    mCamera.stopPreview();
                } catch (Exception e) {
                    // ignore: tried to stop a non-existent preview
                }

                // set preview size and make any resize, rotate or
                // reformatting changes here

                // start preview with new settings
                try {
                    mCamera.setPreviewDisplay(mHolder);
                    mCamera.startPreview();

                } catch (Exception e) {
                    Log.d(TAG, "Error starting camera preview: " + e.getMessage());
                }
            }*/
        }

