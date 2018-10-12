# Stereoscopic rendering in Unity3d for the cave platform

#### Unity 2017.1.2
To enable stereoscopic in Unity3d 2017.1.2 just add the Stereo Display (non head-mounted)
to the Virtual Reality SDK's.  
![Stereo Display (non head-mounted)](/readme-resources/settings-2017-1-2.png)  

#### Unity 2017.2 and later
Due to a undocumented Bug stereoscopic is not longer working.
> XR: Certain aspects of the Vive HMD can be simulated in Editor, without the need of a physical HMD, using the "Mock HMD - Vive" virtual reality SDK in the player settings.
> The mock HMD will use the same asymmetric projection matrix, hidden occlusion mesh, field of view, aspect ratio, and eye texture size as the Vive.
> Mock HMD can be used with both multi and single pass rendering paths.
> Mock HMD will render as a split screen stereo display in Editor.

You can replace Stereo Display (non head-mounted) with Mock HMD - Vive but this option only gives you a split screen as output.
It doesn't work with Nvidia active stereo for 3d vision.  
![Stereo Display (non head-mounted)](/readme-resources/settings-2017-2-later.png)  

Another alternative is to manually add stereoscopic support in your application.
Add `PlayerSettings.stereoscopic3D = true;` (Deprecated in Unity 2017.2) and
`UnityEditorInternal.VR.VREditor.SetVREnabledDevicesOnTargetGroup(BuildTargetGroup.Standalone,new string[] { "stereo" });`
in your code. Now you can select stereo in the settings.    
![Stereo Display (non head-mounted)](/readme-resources/settings-2017-2-manually.png)  

Now run with Unity with `-vrmode stereo` and you should get a stereoscopic output (Resolved in the 2017.2.0P2 patch).

#### Unity 2018
It looks like Unity 2018.2 supports Stereo Display (non head-mounted) again.  
![Stereo Display (non head-mounted)](/readme-resources/settings-2018-2.png)  

#### Other solutions

##### Stereo 360 Capture API
![Stereoscopic 360° API](/readme-resources/stereoscopic-2018-1.jpg)  
Unity 2018 now supports 360° rendering with the new [Stereo 360 Capture API](https://blogs.unity3d.com/2018/01/26/stereo-360-image-and-video-capture/).
It allows to render to a Cubemap in realtime and you can add stereoscopic support with the `Camera.MonoOrStereoscopicEye`
feature ([Unity Documentation](https://docs.unity3d.com/2018.1/Documentation/ScriptReference/Camera.RenderToCubemap.html)).
