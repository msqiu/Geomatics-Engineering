Remote sensing
====
copyright by: Zhouyan Qiu, msqiuzy@outlook.com

## Introduction

Remote Sensing means the sensing of the Earth's surface from space by making use of the properties of electromagnetic waves emitted, reflected or diffracted by the sensed objects, for the purpose of improving natural resources management, land use and the protection of the environment.

Remote Sensing uses the radiant energy that is reflected, emitted or scattered from the earth and its atmosphere from various portions of the electromagnetic(EM) spectrum.

## Basics

### electric and magnetic fields

![Eletromagmentic spectrum](eletromagmentic-spectrum.jpg)

* electrical effects play an important role in the remote sensing

  * Coulomb's law $F=(q_1 q_2)/(4πεr^2 )$. 
  * The permittivity $ε=ε_0*ε_r$, with the electric constant, and is complex and the magnitude varies by the object. For example,  in the mean water level is 81, which is rather large.

* magnetic effects can be neglected in remote sensing

  * In the static magnetic field, ${\vec{B}}=\mu _r∙\mu _0∙\vec{H},$, With $μ_r$ the permeability and $μ_0$ the magnetic constant, and the permeability varies little for the most important types of matter.
  * permanent magnet

### oscillations and waves 

* the difference between oscillation and wave
  
1. Oscillation is the periodical transfer of energy inside the system, two forms: potential energy and kinetic energy.
2. Waves are oscillation propagating through space, which means without oscillation there will be no wave.
3. Waves depend on location, time and transport energy. In another word, waves are classified into transverse and longitudinal while no such classification exists for oscillations.

* wave equation for EM-wave in vacuum

  * the complex natation is advantageous, only real part is of physically of interest
  * angular frequency $ω=2π/T$
  * wave number $k=2π/λ$

* properties of periodic and plane EM waves

  * $E, B, r$ - right hand rule
  * velocity of light
  * transport energy
  * E-field and B-field are in phase
  * plane of E-field oscillation defines polarization plane

* relationship between wavelength and frequency $λ*f=c$  
  velocity of light depends on refraction index at surfaces

* Wave Propagation - Huygens's principle
![Huygens's principle](Huygens-Fresnel_principle.png)
  * Each point on wave front is a source of new elementary wave (diffraction)
  * Wave fronts are interacted by coherent superposition (interference)

### radiation budget

* radiometry
    * measurement of electromagnetic radiance
    * emits radiance depending on its temperature  
      idealized pbject model: Black body(black body radiation)

      * Wien's displacement law: The frequency of maximal radiance is proportional to temperature
      * Stephan-Boltzmann law: The total amount of thermal radiation emitted is directly proportional to the fourth power of its absolute temperature

* radiation Budegt equation $Φ_iλ=Φ_rλ+Φ_aλ+Φ_tλ$

$$
\begin{aligned}
&\rho_{\lambda}=\frac{\Phi_{r \lambda}}{\Phi_{i \lambda}} \quad \text { reflectivity (also reflectance) }\\
&\alpha_{\lambda}=\frac{\Phi_{a \lambda}}{\Phi_{i \lambda}} \quad \text { absorptance }\\
&\tau_{\lambda}=\frac{\Phi_{t \lambda}}{\Phi_{i \lambda}} \quad \text { transmittance }
\end{aligned}
$$

  1. $Φ_iλ$ is the incident (incoming) radiant flux, defined as the amount of energy per unit time (i.e., power).
    $ρ_λ+α_λ+τ_λ=1$
  2. $Φ_rλ$ is the amount of power reflected from the object.
  3. $Φ_aλ$ is the amount of power absorbed by the object.
  4. $Φ_tλ$ is the amount of power transmitted from through the object.

### interaction of waves with matter

#### general remarks
  * the energy of the EM wave is proportional to frequency: $E = h*f$, long wave MW have far less energy than visible light
  * interaction of EM wave with molecules分子
    * optical domain/ infrared (VIS, NIR-FIR): in particular sensitive to chemical object structure
    * thermal radiance TIR热辐射: localize natural and anthropogenic heat sources
    * microwave domain MW: sensitive to conductivity, roughness, morphology

#### diffraction
  * fan out of wave behind obstacles
  * huygens principle
    * every point on the wave front is source of new elementary wave
    * wave front propagates by coherent superposition/ interference
  * Which physical effect determines angular resolution of an imaging sensor? How can we improve such resolution without changing signal wavelength?
  
  ![diffraction](diffraction.jpg)
    1. Diffraction effect determines the angular resolution of an imaging sensor, because the narrower the slit, the more wave will fan out.
    2. angular resolution: $∆θ=1,22*λ/D$, with λ the wave length of signal, and D the antenna size (the optical aperture).
    3. If we want to improve such resolution without changing signal wavelength, we can increase the size of optical aperture 光学孔径

#### absorption/emission
  * energy transfer from wave to matter
  * subtractive color by absorption: CMYK
  * penetration of EM waves into Matter 穿透
    1. penetration proportional to wavelength
    2. microwaves: dependence on moisture 水分

#### scattering
  * change of EM direction at particles in the atmosphere(Molecules, water droplets)
  * the radiance becomes absorbed and is immediately emitted again
  * Energy and wavelength remain the same, direction may change
  * rayleigh-scattering
    1. object size is small compared to wavelength
         * molecules in visible domain
         * raindrops in microwave domain
    2. strongly dependent on wavelength  
      blue sky - shorter blue wavelength scatters more
    3. large wavelength signal can penetrate clouds
  * Mie-scattering  
    Mie scattering is elastic scattered light of particles that have a diameter similar to or larger than the wavelength of the incident light.  
    The Mie signal is proportional to the square of the particle diameter.  
    Mie scattering is much stronger than Rayleigh scattering and, therefore, a potential source of interference for this weaker light scattering process.

#### reflection and refraction
  * Light = Elektro-magnetic Wave
    ![Electromagnetic waves](Electromagnetic_waves.png)  
  * at surface boundaries
  * polarization
    ![polarization](polarization.jpg) 
    1. polarization linear
      * light maybe polarized
      * polarization filter
        * effect of filter depending upon rotation
        * 2 linear polarizing filter with 90 difference in direction - no lights go through
        * 2 linear polarizing filter with any other difference in rotation - intensity reduced
      * separation of stereo images
    2. circular (3D glasses)  
      electric and magnetic field are permanently changing
    3. elliptic
  * velocity of light depends on matter
    * the frequency remains, the wavelength becomes smaller
    * the refraction index is a function of wavelength
    * disperion, prism
  * snell's law of refration: $n1*sin(α)=n2*sin(β)$
  * cause of refraction
    * wave front hits surface oblique
    * dipoles inside matter are forced to oscillate
    * the change of velocity of light causes change of direction
    * brewster's angle
    ![brewster](BrewsterAngle.jpg)  
    * BRDF (Bidirectional Reflectivity Distribution Function): $R(Θ,Φ,θ,φ)$
    * influence of surface roughness
    ![Roughness Criterion](RoughnessCriterion.png)  
      * rough surface - Diffuse reflection is the reflection of light or other waves or particles from a surface such that a ray incident on the surface is scattered at many angles rather than at just one angle as in the case of specular reflection.
      * smooth surface - specular reflection
      * Roughness Criterion: 
$$\sigma_{h}>\frac{\lambda}{8 \cdot \cos (\theta)}$$  
  $σ_h$: the standard deviation of the roughness height regarding to a reference height  
  $θ$: the local incident angle

### various kinds of resolution
* digitalization = sampling and quantization
* sampling
  * spatial resolution
  * spectral resolution
  * temporal resolution
* quantization: radiometric resolution
* the difference between spectral and radiometric resolutions
  * Spectral resolution is the number and width of spectral bands
  * Radiometric resolution tells how many grey values (depends on the number of bits) can be coded, this resolution against to the same spectral band