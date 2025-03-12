using UnityEngine;

public class Player : MonoBehaviour

{
    [SerializeField] private float movingSpeed = 5f;

    private Rigidbody2D rb;

    private void Awake()
    {
        rb = GetComponent<Rigidbody2D>();
    }

    private void FixedUpdate()
    {
        Vector2 inputvector = new Vector2(0, 0);

        if (Input.GetKey(KeyCode.W))
        {
            inputvector.y = 1f;
        }
        if (Input.GetKey(KeyCode.S))
        {
            inputvector.y = -1f;
        }
        if (Input.GetKey(KeyCode.A))
        {
            inputvector.x = -1f;
        }
        if (Input.GetKey(KeyCode.D))
        {
            inputvector.x = 1f;
        }

        inputvector = inputvector.normalized;

        rb.MovePosition(rb.position + inputvector * (movingSpeed * Time.fixedDeltaTime));

    }
}
