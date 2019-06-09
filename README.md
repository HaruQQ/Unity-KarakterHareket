using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class PlayerControler : MonoBehaviour
{
    //karakterin hızını tanımladık
    public float hiz;

    //rigidbody fizik eklentisini tanımladık
    private Rigidbody rb;

    void Start()
    {
        //rigidbody eklentisini getcomponet ile açtık
        rb = GetComponent<Rigidbody>();
    }

    void FixedUpdate()
    {
        //Horizontal yanlara gitmeyi kontrol eder
        float moveHorizontal = Input.GetAxis("Horizontal");

        //vertical yukarı aşağı kontrol eder
        float moveVetical = Input.GetAxis("Vertical");

        //vector 3(x,y,z) değerlerini alır y 0 dedik çünkü yukarı çıkmasını istemiyoruz
        Vector3 hareket = new Vector3(moveHorizontal, 0.0f, moveVetical);

        //burda hareketi hızla çarpıyoruz ki karakter hareket etsin
        rb.AddForce(hareket * hiz);

    }

}
